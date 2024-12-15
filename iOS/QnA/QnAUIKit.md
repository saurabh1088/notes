#  QnA


## 🙋‍♂️1. How would you design a complex UIView hierarchy to ensure optimal performance❓

In order to design a complex UIVIew hierarchy ensuring optimal performance, one requires a blend of
- Thoughtful architecture
- Efficient use of UIKit features
- Performance profiling

Below are some detailed pointers helping achieve a complex UIView hierarchy

### 1.1 Minimize/Flatten the view hierarchy
- Use as few views as possible.
- Avoid deeply nested UIView hierarchies.
    - Pitfall here is that each level adds rendering overhead.
- Use CALayer if interactivity isn't required. CALayer is lighter and faster.

### 1.2 Lazy Loading of Views
- Create and add subviews only when they’re needed, like when they become visible.
- Deallocate or reuse views that move offscreen in scenarios like scroll views or paginated content.
- Conditionally initialize views so that only required views are initialized.

### 1.3 Optimize Auto Layout
- Avoid unnecessary constraints, too many constraints can lead to performance issues.
- Simplify layouts by leveraging intrinsic content sizes and alignment properties.

### 1.4 Reuse views
- Use reusable views, especially in UITableView or UICollectionView as data set could be huge.
- Use reuse identifiers wherever applicable to avoid unecessarily creatinf views.

### 1.5 Optimize Rendering
- If view doesn't needs transparency then keep it opaque.
    - This avoids unecessary calculations required for blending.
- Use backgroundColor and borderWidth instead of custom-drawn backgrounds and borders.
- Avoid overlapping transparent views, as they increase compositing costs.
- Rasterize static layers by using layer.shouldRasterize for views that don’t change often. 
    - NOTE: Be cautious this can increase memory usage.

### 1.6 Efficient Image Handling
- Make sure to use appropriate sized image.
    - This will prevent scaling cost at runtime.
    - If size required is small, using a bigger image incurs more memory cost.
- Images not changing frequently should be cached.
- * Enable UIImageView's contentMode for proper scaling rather than resizing manually.

### 1.7 Optimize Animations
- Limit simultaneous animations to what is visually necessary.
- Use UIView animations for simpler tasks and CoreAnimation (CABasicAnimation, CAKeyframeAnimation) for more complex
animations.
- Avoid creating animations in tight loops or repeatedly triggering them unnecessarily.
- Gracefully handle and close/stop animation once animating view is no longer visible.

### 1.8 Profile and Debug Performance
- Use instruments in Xcode to detect bottlenecks, following in instruments can be used
    - Time Profiler
    - Core Animation FPS
    - Allocations
- Use Xcode’s Debug View Hierarchy to visualize and analyze the hierarchy for inefficiencies.
- Use `Debug > Color Blended Layers` to identify areas with high compositing costs.

### 1.9 Leverage Pre-rendering
- Pre-render static content into a single image (UIImage) and display it in an UIImageView to reduce the number of views
being rendered.
    - This is useful for complex static UI elements like charts or decorative designs.

### 1.10 Manage View Updates
- Perform batch updates
    - For frequent updates, group them together using methods like setNeedsLayout or layoutIfNeeded judiciously to avoid
    redundant recalculations.
- Avoid forced layouts
    - Refrain from calling layoutSubviews or draw(_:) directly. Use system-provided mechanisms to update views.



## 🙋‍♂️2. What is the difference between a `UIView` and a `CALayer`? In what scenarios one would interact with `CALayer` directly❓

### 2.1 `UIView` vs `CALayer`
- In iOS world, every `UIView` is backed by a Core Animation `CALayer`.
- `UIView` is kind of a light wrapper on top of `CALayer`.
- What `UIView` provides on top of `CALayer` is the support for user interaction.
- `CALayer` is available for both iOS and macOS platforms. 
- `CALayer` can be used without `UIView` as well to display content.
- While working with `UIView` one may need to dig in deeper and access `CALayer` in some complex animations.

- Main job of a `CALayer` is to
    - Manage visual content
    - Maintain information about geometry of its content like
        - position
        - size
        - transform

- One can modify properties of `CALayer` to perform animations.

- When working with `UIView`, the `UIView` assigns itself as a delegate to `CALayer`. This relationship cannot be changed.
- When used in isolation, `CALayer`'s delegate object can be provided.
- `UIView` is a container for `CALayer` using UIKit.
- `CALayer` is where actual content is drawn using `CoreGraphics`.

### 2.2 When to use CALayer?
Working directly with `CALayer` doesn't gives any significant performance advantages over `UIView`. One of the reasons
one might want to build a user interface element with `CALayer` instead of `UIView` is that it can be very easily ported
to the Mac. `UIView` is very different from `NSView`, but `CALayer` is almost identical on the two
platforms(iOS and macOS).

#### 2.2.1 Fine-Grained Visual Customizations
- CALayer can be used for
    - Adding shadows
    - Rounded corners 
    - Borders
efficiently.

#### 2.2.2 High-Performance Rendering
- For content-heavy applications (e.g., games or animations), where the overhead of UIView is unnecessary.
    - For e.g. using `CALayer` for lightweight components like particles or custom shapes.

#### 2.2.3 Advanced Animations
- Performing more complex animations which aren't available or possible working with `UIView`.
    - For e.g. 
        - creating keyframe animations
        - path animations, or 
        - animating properties not supported by UIView animations.

#### 2.2.4 Custom Layer Content
- Drawing custom content using `CGContext` for complex graphics.

#### 2.2.5 Layer Backing
- When a `UIView` is not necessary, but one needs a drawable, animatable object.

#### 2.2.6 Offscreen Rendering
- Rasterizing complex views for improved performance.

#### 2.2.7 Non-UI Elements
- Animating or displaying non-UI elements like gradients or masks.


## 🙋‍♂️3. Explain how to create a custom container view controller. What are the use cases for custom container view controllers❓

### 3.1 Implementing a container view controller
`UIViewController` can be subclassed and configured to act like a container view controller. A container view controller
manages the presentation of content of other view controllers it owns. These other view controllers are also known as
its child view controllers. A child’s view can be presented as-is or in conjunction with views owned by the container
view controller.
The container view controller decides
- how many children can be displayed by the container view controller at once
- when those children are displayed 
- where they appear in the container view controller’s view hierarchy
- what relationships, if any, are shared by the children

#### 3.1.1 Setup parent container view controller
This would be a subclass of `UIViewController`. For e.g. `ContainerViewController`

#### 3.1.2 Create and add child view controller
Instantiate and create a view controller which will be the child view controller and add it using API:
`addChild(_:)`
For e.g. `ChildViewController`.
```
let childViewController = ChildViewController()
addChild(childViewController)
```

#### 3.1.3 Add Child's View to Parent's View
Add the child's view to the parent's view hierarchy.
```
childViewController.view.frame = view.bounds
view.addSubview(childViewController.view) // view here is parent viewcontroller's view
```

#### 3.1.4 Notify Child of Addition
Call `didMove(toParent:)` on the child view controller to notify it that it has been added to a parent.
```
childViewController.didMove(toParent: self)
```

#### 3.1.5 Manage Layout if needed
Implement `viewDidLayoutSubviews` or use Auto Layout to adjust the child view's position or size when the parent's view
changes.
```
override func viewDidLayoutSubviews() {
    super.viewDidLayoutSubviews()
    childViewController.view.frame = view.bounds // Or adjust as needed
}
```

#### 3.1.6 Remove Child (if required)
To remove a child, one need to reverse the process done while adding.
```
childViewController.willMove(toParent: nil)
childViewController.view.removeFromSuperview()
childViewController.removeFromParent()
```
### 3.2 Practical Use Cases for Custom Container View Controllers

#### 3.2.1 Split-Screen Layouts
- A container that divides the screen into multiple sections, displaying different content in each.
    - For e.g. a dashboard with charts, tables, and summary widgets.

#### 3.2.2 Custom Tab Bar Interface
- While `UITabBarController` exists, for custom behaviors or appearances, one can implement a custom container to manage
multiple view controllers as tabs.

#### 3.2.3 Wizard or Step-by-Step Processes
- Where one need to guide users through several screens, each managed by its own view controller but under a single
navigation context.

#### 3.2.4 Split View or Master-Detail Interfaces
- Custom containers can manage the relationship between master and detail views, offering more control than
UISplitViewController for specific needs.

#### 3.2.5 Dynamic UI Configurations
- Create flexible layouts where child view controllers can be added, removed, or swapped dynamically based on user
interaction.
    - For e.g. an app where users can drag and drop components to build their own dashboard.

#### 3.2.6 Paging or Carousel-Like Views
- A container that manages horizontal or vertical paging with custom animations or interactions.
    - For e.g. an onboarding screen with a custom page view controller.


## 🙋‍♂️4. How do you implement dependency injection for view controllers in UIKit-based apps❓

### 4.1 Initializer injection
- Inject Dependencies When Creating the View Controller.

### 4.2 Property injection
- Declare dependency as a property and inject it before presentation.

### 4.3 Method injection
- Define a method to accept the dependency and pass the dependency when needed.

### 4.4 Dependency Injection with Coordinators
- In larger apps, one can use a coordinator pattern to manage view controllers and their dependencies.
```
class DependencyContainer {
    let userManager: UserManagerProtocol
    let dataFetcher: DataFetcherProtocol
    
    init() {
        self.userManager = UserManager()
        self.dataFetcher = DataFetcher()
    }
    
    func makeUserViewController() -> UserViewController {
        return UserViewController(userManager: userManager)
    }
}
```

```
class AppCoordinator {
    private let navigationController: UINavigationController
    private let container: DependencyContainer
    
    init(navigationController: UINavigationController) {
        self.navigationController = navigationController
        self.container = DependencyContainer()
    }
    
    func start() {
        let vc = container.makeUserViewController()
        navigationController.pushViewController(vc, animated: true)
    }
}
```

## 🙋‍♂️5. How would you handle scenarios where `viewDidAppear` is called multiple times?❓
- `viewDidAppear` can be called multiple times for various reasons like
    - The view controller is presented modally and then dismissed.
    - The app comes back from the background.
    - A parent view controller's view appears, causing child view controllers to appear.

Below are some ways to handle scenarios when `viewDidAppear` is called multiple times

### 5.1 Check for State Changes
- Use flags or properties to track if certain actions have already been performed.

### 5.2 Use Combine or NotificationCenter
- If scenario is that updates should happen on every appearance but only if certain conditions are met (like data changes),
then one can use Combine to handle these in a reactive way or subscribe to notifications.

### 5.3 Avoid Redundant Operations
- Ensure operations like network requests or heavy computations aren't redundantly performed unless necessary.
- Use flags or conditional checks to prevent this.
- Debounce API calls.

### 5.4 Logging for Debugging
- Log appearances to understand the context in which `viewDidAppear` is being called.
- This can help in debugging unexpected behavior

### 5.5 View Controller Containment
- When using child view controllers or custom container view controllers, `viewDidAppear` will be called for each child
when the parent's view appears. Handle this appropriately by checking parent-child relationships.

### 5.6 Ensure Logic Is Idempotent
- Design code in such a way that multiple executions do not cause unwanted side effects.


## 🙋‍♂️6. What are the different types of segues in `Storyboard`❓

```
For examples refer below project and PR:
https://github.com/saurabh1088/ios/tree/main/LearningAppStoryboardSegueOptionsUIKit
https://github.com/saurabh1088/ios/pull/29
```

- In iOS Storyboards, segues are used to define transitions between view controllers. 
- Following are different types of segues in `Storyboard`

### 6.1 Show (Push)
- For most view controllers, this segue presents the new content modally over the source view controller.
- Viewcontrollers can override and do a custom behaviour.
- A navigation controller pushes the new view controller onto its navigation stack.

### 6.2 Show Detail (Replace)
- This segue is relevant only for view controllers embedded inside a `UISplitViewController` object.
- A split view controller, with this segue will replace its second child view controller (the detail controller) with the
new content.
- When used on view controllers other than `UISplitViewController`, most view controllers will present the new content
modally.

### 6.3 Present Modally
- Presents the destination view controller modally, overlaying the current view controller.
- This can cover the entire screen or appear in a custom presentation style.

### 6.4 Present as Popover
- In a horizontally regular environment(iPad), the view controller appears in a popover.
- In a horizontally compact environment(iPhone), the view controller is displayed using a full-screen modal presentation.

### 6.5 Custom Segue
- A segue that allows custom animations and transitions.
- One need to subclass `UIStoryboardSegue` to define custom behaviour.
- It can be used in scenarios like creating unique transitions that don’t fit the predefined segue types.
    - For e.g. animating a slide-in menu or a fade transition between view controllers.

### 6.6 Unwind Segue
- Used to navigate back to a previous view controller in the storyboard hierarchy.
- The target view controllers must implement an unwind action method.

### 6.7 Embed Segue
- An Embed Segue in a Storyboard is a special type of segue used to establish a parent-child relationship between a view
controller and a child view controller.
- It is most commonly used with container views.


## 🙋‍♂️7. How do you manage data passing between view controllers during these segues❓

### 7.1 Using prepare(for:sender:) method
- The most common way to pass data is by overriding the `prepare(for:sender:)` method in the source view controller.
- This method is called automatically before the segue transition occurs.

### 7.2 Using delegation pattern
- Configure the delegate in `prepare(for:sender:)` method.

### 7.3 Using closures
- Configure the closures in `prepare(for:sender:)` method.


## TODO: In Progress
## 🙋‍♂️8. What is the responder chain in UIKit? How do you use it to handle events or custom actions❓

### 8.1 What is a responder?
- In UIKit, responders are instances of `UIResponder`.
- Importance of responders is that these form the BACKBONE of event handling mechanism in UIKit apps.
- Several key objects in UIKit are responders like
    - UIApplication
    - UIViewController
    - UIView
    - UIWindow
    etc.
- When some event occurs, UIKit dispatches those events to responder objects for handling.
- To handle an event, a responder must override certain methods.
    - For e.g. to handle touch events, a responder must override below
        - `touchesBegan(_:with:)`
        - `touchesMoved(_:with:)`
        - `touchesEnded(_:with:)`
        - `touchesCancelled(_:with:)`

### What is a responder chain?
- As the name indicates, it is a chain of responder objects.
- This chain of objects is responsible for event handling in UIKit.
- The responder chain in UIKit is a mechanism used for event distribution and handling in iOS applications.
- It's essentially a chain of responder objects through which events like 
    - touch,
    - motion, and even 
    - custom actions 
    propagate if they are not handled by the initial recipient.
- A responder object can handle event, but when it doesn't handles an event, it will forward it to next object in responder
chain.
- This responder chain is managed dynamically by UIKit.
- Responders receive the raw event data and must either handle the event or forward it to another responder object.
- When an app receives an event, UIKit automatically directs that event to the most appropriate responder object, known
as the first responder.
- So a responder chain is a dynamic configuration of app's responder objects through which unhandled events are passed
from one object to another till a responder handles the event.

### 8.2 Components of responder chain?

## 🙋‍♂️9. How does responder chain works when view has gesture recognizers❓
In case of gesture recognizers, the gesture recognizer will receive touch and press event before the view on which those
gestures are applied to. From then its the usual responder chain, where if gesture fails to handle event, it goes to view
and further up the responder chain.


## 🙋‍♂️10. Can a responder chain be altered❓
YES, a responder chain can be altered by overriding `next` property of a responder object. Next property is defined as
```
var next: UIResponder? { get }
```
When one sets this property then the next responder is the object that is returned from this property.


## 🙋‍♂️11. What are the differences between `frame`, `bounds`, and `center` properties of a UIView? How does each affect layout and rendering❓

```
For example refer below project and PR:
https://github.com/saurabh1088/ios/tree/main/LearningAppFrameBoundCenterUIKit
https://github.com/saurabh1088/ios/pull/30
```

### 11.1 Frame
Apple's official definition:
*The frame rectangle, which describes the view’s location and size in its superview’s coordinate system.*

```
@MainActor
var frame: CGRect { get set }
```

- The `frame` property is a CGRect that defines the view's location and size in the coordinate system of its superview.

#### 11.1.1 Effect of layout
- Changing the `frame` directly affects the view's position and size relative to its superview.
- Changing `frame` also changes point specified by the `center` property and changes the size in the `bounds` rectangle
accordingly.
- Modifying the `frame`, one is explicitly setting where the view should be in terms of its superview's space.
- Modifying the `frame` changes where the view appears on the screen and its size.
- Moving the `frame.origin` shifts the view’s location relative to its superview.
- Adjusting the `frame.size` resizes the view.

### 11.2 Bounds
Apple's official definition:
*The bounds rectangle, which describes the view’s location and size in its own coordinate system.*

```
@MainActor
var bounds: CGRect { get set }
```

- The bounds property is also a CGRect, but it describes the view's location and size in its own coordinate system.

#### 11.2.1 Effect of layout
- Changing `bounds` affects how content within the view is displayed or how subviews are positioned within this view.
- Altering `bounds.origin` can simulate scrolling or shifting content within the view without moving the view itself in its
superview.

### 11.3 Center
Apple's official definition:
*The center point of the view’s frame rectangle.*

```
@MainActor
var center: CGPoint { get set }
```

- The `center` property is a CGPoint that defines the center point of the view in the superview's coordinate system.
- Apple recommends changing `center` property when one want to change the position of a view.

#### 11.3.1 Effect of layout
- Only the position of the view changes when you adjust center, not its size.
- This is particularly useful for centering views or aligning them relative to other views by manipulating their center
points.
- Changing the `center` moves the view to a new position in its superview, without affecting its size.

### 11.4 Rendering and Layout
- The `frame` determines the region occupied by the view in the superview.
- The `bounds` affects the content displayed within the view.
- The `center` simplifies alignment tasks when positioning the view.


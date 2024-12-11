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


## 🙋‍♂️4. ❓


## 🙋‍♂️5. ❓


## 🙋‍♂️6. ❓


## 🙋‍♂️7. ❓


## 🙋‍♂️8. ❓


## 🙋‍♂️9. ❓


## 🙋‍♂️10. ❓


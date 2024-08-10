# SwiftUI

## Observation in SwiftUI

### Source
WWDC 2023
Discover Observation in SwiftUI
https://developer.apple.com/videos/play/wwdc2023/10149/

### What is Observation?
Observation is a new Swift feature announced in WWDC 2023 for tracking changes to properties. It works with normal Swift types and transforms them with the magic of macros.
This feature lets one to define application’s models using standard Swift syntax and uses those types to have UI respond to changes to that model.
The `@Observable` tells the Swift compiler to transform code from what was written to an expanded form that makes the type able to be observed.

When a SwiftUI’s body is executed, SwiftUI tracks all access to properties used from `Observable` types. It then takes that tracking information and uses it to determine when the next change to any of those properties on those specific instances will change. When the change happens, the view is invalidated and re-drawn.

The general rule for Observable is, if a property that is used within view’s body changes, the view will update.

### What about computed properties?
Adding in a computed property follows those same rules as before. When a property that is used changes, the UI updates.
So if the computed property is computed based of some property which changes, then the usage of computed property in the view body will lead to view updation.

With Observable, the property wrappers for SwiftUI are even easier than ever.
- @State, 
- @Environment, and 
- @Bindable
are the three primary property wrappers for working with SwiftUI.

### Usage of @State, @Environment and @Bindable
- @State : Use when the view needs to have its own state stored in a model.
- @Environment : Environment lets values be propagated as globally accessible values. This lets things be shared in many places. Observable types work fantastically here since the updates created by them are based upon access.
- @Bindable : Newest member, the bindable property wrapper is very lightweight. All it does is to allow bindings to be created from that type using $ syntax.

For using wrappers while working with a model using observables, one need to ask three questions
- Does this model need to be state of the view itself? If so, use `@State`. 
- Does this model need to be part of the global environment of the application? If so, use `@Environment`. 
- Does this model just need bindings? If so, use the new `@Bindable`.
If none of these questions, answers as yes, then use the model as a property of the view.

### One can achieve similar result with ViewModifier and Views, which approach to use when?
Example explored at below location:
https://github.com/saurabh1088/SwiftUI/blob/main/SwiftUILearnings/TestPitch/ViewVSViewModifierExampleView.swift


## TODOs

1. **SwiftUI Basics**
   - Understanding the SwiftUI framework
   - Views and view composition
   - Modifiers and view customization
   - Layout and geometry

2. **State Management**
   - @State, @Binding, and @StateObject
   - ObservableObject and @Published
   - EnvironmentObject and @Environment
   - Using Combine with SwiftUI

3. **Navigation and App Structure**
   - NavigationView and NavigationLink
   - TabView and TabItem
   - Presentation and sheets
   - Deep linking and programmatic navigation

4. **Data Handling and Persistence**
   - Fetching and displaying data from APIs
   - Core Data integration with SwiftUI
   - Using Combine for asynchronous data handling

5. **User Input and Forms**
   - Handling text input and forms
   - Validating user input
   - Custom controls and interactions

6. **Animations and Transitions**
   - Implicit and explicit animations
   - Custom animations and transitions
   - GeometryEffect and AnimatableModifier

7. **Styling and Theming**
   - Customizing view appearance
   - Dark mode support
   - Creating reusable style components

8. **Accessibility**
   - Ensuring accessibility support
   - VoiceOver and dynamic type
   - Accessibility modifiers and tools

9. **Advanced SwiftUI Concepts**
   - Custom view modifiers
   - PreferenceKey and GeometryReader
   - Custom containers and layout

10. **Interoperability**
    - Integrating UIKit with SwiftUI
    - Using UIViewControllerRepresentable and UIViewRepresentable

11. **Testing and Debugging**
    - Unit testing SwiftUI views
    - Snapshot testing
    - Debugging tools and techniques

12. **Performance Optimization**
    - Identifying and optimizing performance bottlenecks
    - Efficient use of resources and memory management
    - Profiling and analyzing SwiftUI applications

13. **Architectural Patterns**
    - MVVM (Model-View-ViewModel) pattern
    - Coordinator pattern
    - Dependency injection

14. **Concurrency**
    - Using async/await with SwiftUI
    - Managing background tasks and updates

15. **Networking**
    - Integrating RESTful APIs
    - Handling networking errors
    - Using URLSession and other networking libraries

16. **App Lifecycle and State Restoration**
    - Managing app lifecycle events
    - State restoration and scene management

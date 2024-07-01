#  SwiftUI

## Source
Work with windows in SwiftUI
https://developer.apple.com/videos/play/wwdc2024/10149/

Windows are container for the content of an app. A window allows people to manage parts of an app with familiar controls like :
- reposition
- resize
- close

Multi- window platforms
- iPadOS
- visionOS
- macOS


Fundamentals
- With multiple windows user can use different parts of an app at the same time.
- Each window can take advantage of platform specific features
- Placement
    - One can provide an initial placement for for example when a new window is created
- Sizing
    - One can size window and should size window based on the content


## Source
Demystify SwiftUI containers
https://developer.apple.com/videos/play/wwdc2024/10146/


### ViewBuilders
- Support composing any type of views together within the same container
- Allows content to be defined 
    - statically by passing all views 
    - dynamically by using ForEach loop


### Examples of SwiftUI Containers
- List
- Group


### Session explains about building custom container views for SwiftUI
- SwiftUI has many container views
- Container views provide a trailing closure view builder argument.


### Custom Containers
- Composition
    - Example of composition in List : Construct List with static content using Text view and also dynamic content using iteration over ForEach within same container.
    - ForEach(subViewOf:) is ✨NEW API this year. This accepts a single view value as input and passes back each of it’s subviews into the trailing closure view builder, giving opportunity to transform them into different kind of view.
    - ForEach(subviewOf:) : What is a subview? : Well subview is a view contained within another view. Static views form the declared subviews, which includes the ForEach without counting the views within the ForEach. Views which finally appear on screen, which in case of ForEach may turn out to be more as per content, will be called resolved subviews. Declared subviews in SwiftUI defines a recipe which will produce the resolved subviews when the app is running. For example the ForEach subview is a declared subview which doesn’t have any specific visual appearance of its own. But the purpose of ForEach is to produce a collection of resolved subviews.
    - Group is also an example of built-in container and represents a collection of resolved subviews.
    - EmptyView is a declared view, which resolves to no subview.
    - ForEach(subViewOf:) : This API iterates only over the resolved subviews of the container.
    - Group(subviewsOf:) NEW API. Just like ForEach(subviewOf:), this API also accepts a view as input and resolves its subviews, however instead of iterating over subviews one at a time, it passes back a collection of all of the resolved subviews.
- Sections
    - List is a SwiftUI’s built in container which supports adding Sections using SwiftUI’s Section view.
    - Custom containers don’t support adding sections by default
    - ForEach(sectionOf:) ✨NEW API
        - This API iterates over each section of view it detects.
- Customization
    - Container Values : ✨NEW API for building container specific modifiers.
    - Container Values are a new kind of keyed storage, similar conceptually to environment and preferences. Now environment values are passed down the view hierarchy, whereas preferences are passed up the view hierarchy. Container Values of a resolved view can only be accessed by its direct container.
    - To define a container value, one needs to
        - Create an extension of ContainerValue : ContainerValue is a ✨NEW type this year.
        - Create a property using @Entry macro : @Entry macro is a ✨NEW API
        - Declare a custom view modifier for setting the defined property. This calls through new .contanerValue() API modifier.
        - Next modify the subviews from container by reading in the container values.
        - Container Values can be read from resolved subviews and sections both.

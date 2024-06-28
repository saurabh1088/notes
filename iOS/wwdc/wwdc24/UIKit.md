#  UIKit


## Source
What’s new in UIKit
https://developer.apple.com/videos/play/wwdc2024/10118/

- Document launch experience
- Updated tab and sidebar
    - New look and feel
    - When minimised, the sidebar animates back to tab bar
    - Adapt for native experience on Mac Catalyst and visionOS
    - For more check https://developer.apple.com/videos/play/wwdc2024/10147
- Fluid transitions
    - New zoom transition which works both for navigation and presentation


## UIKit and SwiftUI Interoperability
- Animations
    - Now one can use SwiftUI animation type to animate UIKit views.
    - UIView.animate(.interactiveSpring) { }
    - For more check https://developer.apple.com/videos/play/wwdc2024/10145
- Gesture Recognizers
    - UIKit & SwiftUI’s gestures are unified
    - One can add UIKit gesture recognisers to SwiftUI seamlessly using UIGestureRecognizerRepresentable protocol


## Some General enhancements
- Automatic trait tracking
    - Trait system propagates data to the view controllers and views in app’s hierarchy
    - Now UIKit supports automatic trait tracking in common views and view controller update methods like layoutSubviews()
    and drawRect()
    - UIKit tracks which traits are being used and when any of those trait changes it automatically performs associated invalidation
    - Before automatic trait changes, one would need to register for trait changes and call a designated selector
    - Automatic trait tracking delivers maximum performance
    - This feature is always active for supported methods  
- List improvements
    - All views in UICollectionView list sections and UITableViews now have listEnvironment trait set
    - listEnvironment trait is a new trait this year
    - This listEnvironment describes the style of list that view is in.
    - One can use this trait to ensure that the cells are styled appropriately in any given list
- Update link
    - UIUpdateLink is new in iOS 18
    - Automatic view tracking
- Symbol animations
    - SF Symbol animations
- Sensory feedback
    - Attach feedback generators to view
    - New UICanvasFeedbackGenerator
    - UICanvasFeedbackGenerator is created and associated with a view with location passed to it, now using for eg. with
    Apple Pencil one can get haptic feedback
- Text improvements
    - New menu options in edit text, for apps which allows text editing
    - This new options bring in new formatting panel with default set of options
    - Formatting option makes it easy to change font, size etc and also highlighting the text.
- Menu actions
    - New this year in iOS 18, add menu actions to iPhone apps. Following commands can be invoked by system to control apps
        - UICommand
        - UIKeyCommand
        - UIAction
    - Refer https://developer.apple.com/videos/play/wwdc2021/10057 for more details
- Apple Pencil
    - Squeeze gesture
    - Configure PKToolPicker
    - Add custom tools

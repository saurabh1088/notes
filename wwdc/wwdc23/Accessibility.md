# Accessibility


## Accessibility audits for app

### Accessibility Audits

Xcode ships with accessibility inspector which can help audit app for several
accessibility issues and can help to fix those.
Accessibility audits are powerful and now there are automatable as well.

_Now we can perform accessibility audits in UI tests_

```app.performAccessibilityAudit()```

There is no need for any assertions for these tests, test will automatically fail
for issues found.

If UI tests can find ui elements, so can assistive technologies. This means UI tests
checking if ui element exists or not also end up testing if the element is accessible
or not.

performAccessibilityAudit also takes input of categories for which accessibility
audit should be performed.


## Accessibility enhancements

1. New accessibility trait isToggle, available for both SwiftUI & UIKit
```
            .accessibilityAddTraits(.isToggle)
            
            .accessibilityTraits = [.toggleButton]
```

2. Accessibility Notifications are new API providing a unified, multi platform way
to create announcements to convey information. These can be create for apps running
on using SwiftUI, UIKit and AppKit. It can send notifications regarding
    - Announcement
    - LayoutChanged
    - ScreenChanged
    - PageScrolled
    
```
                AccessibilityNotification.Announcement("Loading").post()
```

One can also set priority for announcement as: 
- High (Can interrupt, Can't be interrupted)
- Default (Can interrupt, Can be interrupted)
- Low (Can be interrupted)

```
        .accessibilitySpeechAnnouncementPriority = .low
```

3. New modifier added for accessibility zoom action
```
            .accessibilityZoomAction { action in
                
            }
```

4. Direct touch trait named allowsDirectInteraction. In default state voice over 
both speaks and activates the content. For say a piano app, it would be nice for
voice over to immediately play sound on tap action instead of speaking about the
tapped key.
- Silent on touch
- Requires activation 

```
        .accessibilityDirectTouch(options: .silentOnTouch)
```


## Improve accessibility visual

Accessibility content kind controls appearance of accessibility elements on screen.
Previously there was interaction content shape kind which changes both the accessibility
shape and hit testing shape.
Now there is accessibility content shape kind which will not impact hit testing
shape, it will only impact the shape of accessibility content.
Accessibility shape kind when applied to a view will update underlying accessibility
geometry for the element with the shape provided

```
            .contentShape(.accessibility, Circle())
```

## Keep state up-to-date

Block based attribute setters
- Keeps underlying accessibility attributes updated
- Provides a closure for attributes
- Closure is evaluated everytime view is referenced


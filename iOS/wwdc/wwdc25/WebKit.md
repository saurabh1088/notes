#  WebKit

Source : https://developer.apple.com/videos/play/wwdc2025/231/

## Overview

- WebKit is the browser engine powering Safari, Mail, and many apps across Apple platforms (iOS, iPadOS, visionOS, macOS).
- Enables developers to build rich, dynamic web experiences within apps, leveraging Apple platform strengths.


## WebKit for SwiftUI

- New SwiftUI API makes integrating web content into apps easier than ever.
- WebView: A new SwiftUI view for displaying web content by providing a URL.
- Works across all platforms supported by WebKit.


## Loading and Displaying Web Content

- WebView can display content from a URL and automatically updates when the URL changes.
- WebPage: An Observable class representing web content, designed for Swift and SwiftUI.
- WebPage can load remote URLs, HTML strings (with base URL), and data (e.g., web archives) directly.


## Local Resources and Custom URL Schemes

- URLSchemeHandler protocol allows loading content bundled in the app or from local files.
- Custom schemes (e.g., `lakes`) can be handled by implementing URLSchemeHandler and registering it with WebPage configuration.
- Enables pre-populating apps with bundled HTML/CSS assets.


## Observing and Responding to Navigation

- WebPage exposes an observable `currentNavigationEvent` property for tracking navigation state.
- Navigation events include: started, redirected, committed, finished, failed.
- Swift 6.2 Observations API can be used to react to navigation changes asynchronously.
- Other observable properties: page title, current URL, loading progress, theme color.


## Communicating with Web Content

- JavaScript can be evaluated directly using the `callJavaScript` API.
- Supports passing arguments and receiving results, enabling flexible interaction with web content.


## Customizing Navigation Policies

- WebPage.NavigationDeciding protocol allows custom navigation policies.
- Can allow or cancel navigations based on URL schemes or hosts (e.g., open external links in the default browser).
- Navigation decisions can be handled before navigation, on response, or when authentication is needed.


## Enhancing User Interaction with View Modifiers

- `scrollBounceBehavior`: Customize scroll bouncing (vertical/horizontal) in WebView.
- On visionOS, `webViewScrollInputBehavior` enables look-to-scroll interaction.
- `findNavigator`: Adds Find-In-Page support, integrated with platform-specific UI.
- `webViewScrollPosition`: Syncs scroll position with app state, enabling features like sidebar section navigation.
- `onScrollGeometryChange`: Observes scroll geometry changes to update UI (e.g., syncing sidebar selection with scroll position).


## Summary

- WebKit for SwiftUI provides a simple yet powerful API for integrating and customizing web content in apps.
- Supports loading remote and local resources, observing navigation, communicating with JavaScript, and customizing user interactions.
- Powerful view modifiers enhance the user experience and accessibility.
- Recommended to refer to Developer Documentation for more details and to explore new Swift and SwiftUI features like Observations API.
- Encouraged to migrate from UIKit/AppKit WebKit APIs to the new SwiftUI API and provide feedback.

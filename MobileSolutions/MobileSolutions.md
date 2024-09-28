# Mobile Solutions

## Native Solutions

### iOS

Tech stack : 
- Swift & Objective C as programming language
- SwiftUI & UIKit as UI frameworks
- Xcode as IDE

### Android

Tech stack : 
- Kotlin & Java as programming language
- Jetpack Compone & XML as UI frameworks
- Android Studio as IDE

## Hybrid Solutions

### Apache Cordova

Tech stack : 
- HTML, CSS, JavaScript
- JavaScript frameworks can be used like angularJS
- Cordova plugins are used to access native capabilities

Apps developed using Apache cordova are technically web apps built using web technologies like HTML, CSS and JavaScript.
The resulting app running on mobile devices is technically a web app running inside a native container's webview. All the
UI layer is developed using HTML CSS and JavaScript, business logic is written using JavaScript. This whole web artifacts
are bundled withing the app bundle. In order to access device capabilities like camera, there are cordova plugins which
can be used.

Pros :
- Technically a web app, so if solution already has a web version, it can be re-used and saves effort.

Cons :
- Microsoft App Center announced withdrawing support from Apache Cordova. This puts distribution of apps using apache cordova
in unknown state.
    - https://devblogs.microsoft.com/appcenter/announcing-apache-cordova-retirement
- Waning developer community support.
- Newer frameworks like Flutter and ReactNative are now more preferred.
- Dependency on cordova plugins for accessing device capabilities.

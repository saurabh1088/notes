# oAuth2.0

This document covers oAuth2.0 implementation in iOS.
For detailed discussion on oAuth2.0 in general refer:
https://github.com/saurabh1088/notes/blob/main/oAuth/oAuth.md



## Implementing oAuth2.0 in iOS

For implementing oAuth2.0 flow in an iOS app one need to take care of below steps.

1. oAuth Provider
There need to be some oAuth provider selected for the application for example Google, Facebook, GitHub etc.

2. Register app with oAuth Provider
The app requiring oAuth2.0 implementation need to be registered with the oAuth provider. This process is usually on some
console provided by oAuth provider where one can add the application and obtain a *client ID* and *client secret*

3. Update App for redirect URL



## Libraries in iOS for oAuth2.0 Flow

1. AppAuth
https://github.com/openid/AppAuth-iOS

AppAuth library is available for following Apple platforms:
- iOS
- macOS
- tvOS

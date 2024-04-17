# Background Assets

Source WWDC 2022 Video : https://developer.apple.com/videos/play/wwdc2022/110403


## What is Background Asset?
Background Asset is a Framework.


## Problem Background Asset addresses
One waits to download an App from appstore. Depending upon size it can take a while. Once installed, sometimes apps need
to download some additional content once user launches the app. this again present user with a progress bar or something
indicating download activity which is not a great user experience. It could be great to have ready before user launches
the app.
Background Asset aims to ensure that content is present by the time app is launched.


## Objectives of Background Asset Framework
1. Enrich user experience of apps.
2. Flexible with existing workflows with any complex asset management systems one is already using.
3. Provides ability to schedule and update assets outside of the app's lifecycle.
4. Can be used in scenarios where some large assets need to be downloaded before using app.


## Magic Behind
For Background Asset's use case, a new app extension is created to download content in background. This new extension is
built on top of app extension technology. Extension enable the opportunity to run code outside of the app's lifecycle.

This extension will run when :
1. User first installs the app, but hasn't launched yet.
2. App is updated automatically in the background.
3. Periodically in background, to check updated assets and schedule them periodically over time.
This approach ensures that whenever user will open the app after install or update, content gets downloaded.


## Adopting Background Asset Framework
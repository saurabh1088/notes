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

Download Manager(BADownloadManager) is the PoC from the Framework which is used to communicate. This manager is a
Singleton and can be used throughout the app using Background Asset framework.
This manager can be used to :
- schedule the download of asset in Foreground (This can only be done from App, not from the extension)
- schedule the download of asset in Background
- Retrieve downloads currently in flight, might have started before the app was launched
- Cancel downloads

There is a synchronisation mechanism which manages exclusive access between the app and the extension so that both should
not end up scheduling or modifying existing downloads at same time.

How to set up and start using Background Asset framework
- Import the framework
- Set up the URL with the location of asset to be downloaded
- Define app group container which contains both the app and the extension
- Create download object, for example the most common one is BAURLDownload


BAURLDownload initialiser takes an identifier along with URL and app group identifier. The identifier(not the app group
one) will be used to track download across multiple launches of the app.
These identifiers needs to be unique as the engine will not allow more than one download to be scheduled with same
identifier.

One can fetch list of all downloads currently in progress or scheduled.

Delegate receives messages for all the downloads scheduled by app or extension. Callbacks will be received for all downloads so one needs to use identifiers to distinguish among those.
If app doesn’t defines a delegate to handle message, then the extension will wake up to process the message. This implies one should expect extension to be sent messages.
Extension will be woken only for common interfaces where app fails to handle messages. A download succeeding or failing is an example of a common interface between the delegate and the protocol.
If the extension is currently running, it can use BADownloadManager and establish a delegate. This will allow both the app and extension to receive duplicate messages to their delegates, but only if extension was running, it will not wake up if not running.

File once downloaded will be placed at location system provides.
Apple strongly recommend that you leave the file at the location that the system has provided.
Only move the file if you absolutely must and please do not duplicate it unless you delete the originating file afterwards.

The extension! The extension enables you to schedule the downloads of your assets before the user has launched your app.

The extension also runs periodically based on how often a user uses your app.
If someone uses your app everyday, then the system learns this behavior and your extension will run more frequently.

Background download extension is different from other app extensions as it is brokered by the system instead of app being responsible for talking to extension.
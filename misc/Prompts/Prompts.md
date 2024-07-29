# Prompts

```
Design an iOS application login module which uses end user's google account to sign-in. Design should include the following:
- high level design
- low level design. 
Additionally explain:
How oAuth2.0 will be implemented?
How authorisation server and auth provider will be setup?
What all API end points will be required?
Consider using oAuth2.0 authorisation code grant flow.
After explaining design, desribe detailed user journeys covering all possible user flows.
```

```
Describe the entire process for adding a push notification capability to an iOS App. Notification authorisation prompt
shouldn't be asked at app launch, but at some point later in flow.
Include in the process:
- How to add capability to app
- What all certificates, profiles will be required and how to generate those.
- How to setup provider server for communication with APNs
- How to send push notifications to for example millions of users
- How to send push notifications to a certain users, for example users of a specific location or iOS version
- How to design and send rich notifications
```

```
Explain how to create a sample iOS Application with push notification capability. Push notification need to be a rich
notification which includes images and videos. Also before pushing app to appstore, need to test the rich notification
locally preferably on iOs simulator. Explain process on how to test this rich notification using Xcode and iOS simulator.
```

```
An iOS App need to download some content from a remote server. Implement this scenario using URLSession. 
- How the download task will be performed?
- Which APIs from URLSession will be used?
- What kind of wrapper over URLSession can be made.
- How to handle the UI when download starts?
- How to show the progress of download on UI?
- How to save the downloaded file on device?
- How to show file is downloaded already and prevent re-trigger of download?
- How to handle scenario where network is lost and download is not completed, how to recover from that once network is available back?
- How to continue download when app goes to background?
- Or what happens when app is killed with some download is in progress?
```

```
What are different states of an iOS app?
- List each state
- Give examples how, when and under what condition each state is achieved for an app.
- Provide scenarios like what happens to states when say a notification is received, or a call is received.
```

```
How to setup a core data stack with multiple managed contexts. Also give practical use cases why a multiple managed
context could be required 
```

```
Explain and discuss in details why should an iOS application written using Swift language should use Alamofire for
networking instead of using Apple's URL Loading System.
- What are specific use cases which calls for using library Alamofire.
- Don't list reasons like the library is tried and tested and it will reduce development time and effort.
- Reasons in favour should purely be derived from practical use case and from the functionalities Alamofire provides over
URL Loading System.
```
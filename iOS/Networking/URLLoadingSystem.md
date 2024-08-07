#  URL Loading System


 ## URL Loading System & it's players
 
 *For examples check : https://github.com/saurabh1088/swift-playgrounds/blob/main/Networking.playground/Contents.swift*
 
 In a nutshell one creates a `URLSession` instances which is then used to create one or more `URLSessionTask` instances
 which can fetch and return some data, download or upload files. Session is configured using a `URLSessionConfiguration`
 object controlling ths behaviour in general.
 
 ### URLSession
 Usually an app may create one or more `URLSession` instances, which help in coordinating group of related data-transfer
 tasks. For e.g a web browser app might create one instance for each browser tab. A separate instance might be required
 for creating an ephemeral browsing session.

 So basically a `URLSession` instance is created (or more than one if needed). The instance gives capabilities(APIs) to
 perform tasks. All the tasks which a `URLSession` instance performs or will perform will share same a common
 configuration object. This configuration object is `URLSessionConfiguration`
 
 `URLSession` is the key object which one uses for sending requests and receiving responses.

 One can create different kinds of `URLSession` instances like :-

 - `URLSession` provides a singleton shared instance (*URLSession.shared*).
   - This shared instance doesn’t have any configuration object
   - One can't set any configuration object to it
   - hence is not customisable but will serve a good starting point for most simple use cases.
 - `URLSession` instance initialised and configured with a default `URLSessionConfiguration` object
 - `URLSession` instance initialised and configured with a ephemeral `URLSessionConfiguration` object
 - `URLSession` instance initialised and configured with a background `URLSessionConfiguration` object which allows
 background operations


 Using a `URLSession` instance ultimately allows us to create tasks. These tasks eventually perform one of the below operations

 1. Data tasks
    - using *Data* objects
    - these are for short often interactive requests to a server
 2. Upload tasks
    - send data in form of file
    - support background uploads
 3. Download tasks
    - retrieve data in form of file
    - support background downloads and uploads
 4. Websocket task exchange
 
*sessionDescription*
There is a sessionDescription property of URLSession instance, which one can set. This can be used to set a human readable
string to make is identifiable for debugging purposes. The value for sessionDescription is nil by default. Value if set will
be visible in HTTP Traffic as viewed in instruments.

 ### URLSessionDelegate

 Tasks in a `URLSession` instance share a common delegate object i.e. `URLSessionDelegate`.
 `URLSessionDelegate` defines methods `URLSession` instance will call on it’s delegate to handle session-level events.
 `URLAuthenticationChallenge` is received as a part of `URLSessionDelegate`.
 `URLSession` instance can be created without a `URLSessionDelegate` as well.


 `URLSession` APIs are highly asynchronous. There are APIs available to use with following usual ways of asynchronous programming
 - async/await
 - completion handler
 - delegate callback


 ### URLSessionConfiguration

 `URLSessionConfiguration` object help defining the behaviour and policies when using a `URLSession` instance for networking. One can establish various behaviours, for example :
 - Caching policy
 - Timeouts
 - Supporting Multipath TCP - multipathServiceType
 - Additional HTTP headers


 When `URLSession` instance is initialised, a `URLSessionConfiguration` object can be passed.
 This `URLSessionConfiguration` object `URLSession` will copy and further no changes can be made.
 This implies once a `URLSession` instance is configured for a `URLSessionConfiguration` then the
 only way to change configuration is to create a new `URLSession` instance. So the configuration object
 `URLSessionConfiguration` should be setup very carefully.
 
 *Delegates*
 `URLSession` has a `delegate` property to which any type conforming to `URLSessionDelegate` can
 be assigned. There are several other delegates as well which play some part in URL loading system.
 
 - `URLSessionDelegate`
    - `URLSessionTaskDelegate`
        - `URLSessionDataDelegate`
        - `URLSessionDownloadDelegate`
        - `URLSessionStreamDelegate`
        - `URLSessionWebSocketDelegate`
 
 
 `URLSessionTaskDelegate` inherits from `URLSessionDelegate`.
 `URLSessionDataDelegate`, `URLSessionDownloadDelegate`, `URLSessionStreamDelegate`
 & `URLSessionWebSocketDelegate` all inherit from `URLSessionTaskDelegate`
 
 ### resume()
 
 When a data task is created using a session object, the task created is by default created in a suspended state. One need
 to start is calling `resume()`

## Cache Policy

There are available different caching strategies governed by cache policies which can help improve performance and
reduce network traffic for application.

### URLSessionConfiguration requestCachePolicy

*Default value of requestCachePolicy is useProtocolCachePolicy*

This instance property for `URLSessionConfiguration` will determine when to return a response from cache. As this property
is for `URLSessionConfiguration` instance hence it will affect the entire session, including how caching is handled
globally for all requests made within that session.

So all requests made under session with some cache policy set using requestCachePolicy
on `URLSessionConfiguration` will get same cache policy unless a request uses it's
own policy which is covered below in URLRequest.

### URLRequest cachePolicy

Cache policy set at `URLRequest` will override the one defined in `URLSessionConfiguration`
so this comes in handy if for certain requests one want a different behaviour.

### URLCache

- `URLCache` is used for caching responses from network resources.
- URLSessionConfiguration has `urlCache` property which is of type `URLCache`, this
property determines the URL cache object used.
- `URLCache` basically maps a URL request to response object.


## Timeouts

### How can one configure and handle timeouts while using URL Loading System?

1. One can set below properties of URLSessionConfiguration object :
- timeoutIntervalForRequest
- timeoutIntervalForResource

2. One can handle timeout for each request by using URLRequest's *timeoutInterval* property. Default value is 60 seconds.


## QnA

### An iOS app was downloading some data using URLSession, what will happen if user puts app to background?
### Will the download continue?
If the app was using URLSeesion with a configuration object not configured for background tasks, then the download task
will be suspended. To allow an iOS app to have background uploads or downloads capability, one needs to create
`URLSessionConfiguration` using type method `background(withIdentifier:)`.
When a session object is created configured with `URLSessionConfiguration` created with `background(withIdentifier:)`, it
allows session object with capability to hand over control of uploads or downloads to system, with system taking those in
separate process. This capability allows an app to continue uploads/downloads with app moving to background or even if it
gets terminated.
- NOTE : Suspended tasks are not resumed automatically once app returns to foreground, one need to handle resuming any
suspended tasks if required.


### An iOS App was downloading some data using URLSession, what will happen when app is terminated?
### Does it makes any difference if the app is terminated by user or by system?
If the app was using URLSeesion with a configuration object not configured for background tasks, then the download task
will be cancelled. To allow an iOS app to have resume uploads or downloads after quit, one needs to create
`URLSessionConfiguration` using type method `background(withIdentifier:)`.
When a session object is created configured with `URLSessionConfiguration` created with `background(withIdentifier:)`, it
allows session object with capability to hand over control of uploads or downloads to system, with system taking those in
separate process. This capability allows an app to continue uploads/downloads with app moving to background or even if it
gets terminated.
- NOTE : This behaviour applies only if the app was terminated by system. If user themselves terminate apps, then upload and
downloads tasks get cancelled.
- NOTE : System, if terminates app, will not automatically relaunch it. Any upload or download tasks which were terminated
and were correctly configured to have background performance capabilities will be resumed once user opens app again.


## TODOs

- [ ] 1. Instruments to analyze HTTP Traffic
      - Ref doc : https://developer.apple.com/documentation/foundation/url_loading_system/analyzing_http_traffic_with_instruments

- [ ] 2. Explore data upload and download tasks, what will happen when network is lost while upload and download is in progress
- [ ] 3. Upload/Download tasks scenarios while app goes to background or is killed, what needs to be done.
- [ ] 4. Check usage and difference in timeoutIntervalForRequest and timeoutIntervalForResource

#  URL Loading System

 ## URL Loading System & it's players
 
 
 *For examples check : https://github.com/saurabh1088/swift-playgrounds/blob/main/Networking.playground/Contents.swift*
 
 In a nutshell one creates a *URLSession* instances which is then used to create
 one or more *URLSessionTask* instances which can fetch and return some data, 
 download or upload files. Session is configured using a *URLSessionConfiguration*
 object controlling ths behaviour in general.
 
 ### URLSession

 Usually an app may create one or more *URLSession* instances, which help in coordinating 
 group of related data-transfer tasks. For e.g a web browser app might create one 
 instance for each browser tab. A separate instance might be required for creating 
 an ephemeral browsing session.

 So basically a *URLSession* instance is created (or more than one if needed). 
 The instance gives capabilities(APIs) to perform tasks. All the tasks which a 
 *URLSession* instance performs or will perform will share same a common configuration 
 object. This configuration object is *URLSessionConfiguration*
 
 *URLSession* is the key object which one uses for sending requests and receiving responses.

 One can create different kinds of *URLSession* instances like :-

 - *URLSession* provides a singleton shared instance (*URLSession.shared*). This shared instance doesn’t have any configuration object so is not customisable but will serve a good starting point for simple use cases.
 - *URLSession* instance initialised and configured with a default *URLSessionConfiguration* object
 - *URLSession* instance initialised and configured with a ephemeral *URLSessionConfiguration* object
 - *URLSession* instance initialised and configured with a background *URLSessionConfiguration* object which allows background operations


 Using a *URLSession* instance ultimately allows us to create tasks. These tasks eventually perform one of the below operations

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


 ### URLSessionDelegate

 Tasks in a *URLSession* instance share a common delegate object i.e. *URLSessionDelegate*.
 *URLSessionDelegate* defines methods *URLSession* instance will call on it’s delegate to handle session-level events.
 *URLAuthenticationChallenge* is received as a part of *URLSessionDelegate*.
 *URLSession* instance can be created without a *URLSessionDelegate* as well.


 *URLSession* APIs are highly asynchronous. There are APIs available to use with following usual ways of asynchronous programming
 - async/await
 - completion handler
 - delegate callback


 ### URLSessionConfiguration

 *URLSessionConfiguration* object help defining the behaviour and policies when using a *URLSession*
 instance for networking. One can establish behaviour for example :
 - Caching policy
 - Timeouts
 - Supporting Multipath TCP - multipathServiceType
 - Additional HTTP headers


 When *URLSession* instance is initialised, a *URLSessionConfiguration* object can be passed.
 This *URLSessionConfiguration* object *URLSession* will copy and further no changes can be made.
 This implies once a *URLSession* instance is configured for a *URLSessionConfiguration* then the
 only way to change configuration is to create a new *URLSession* instance. So the configuration object
 *URLSessionConfiguration* should be setup very carefully.
 
 *Delegates*
 *URLSession* has a *delegate* property to which any type conforming to *URLSessionDelegate* can
 be assigned. There are several other delegates as well which play some part in URL loading system.
 
 - *URLSessionDelegate*
    - *URLSessionTaskDelegate*
        - *URLSessionDataDelegate*
        - *URLSessionDownloadDelegate*
        - *URLSessionStreamDelegate*
        - *URLSessionWebSocketDelegate*
 
 
 *URLSessionTaskDelegate* inherits from *URLSessionDelegate*.
 *URLSessionDataDelegate*, *URLSessionDownloadDelegate*, *URLSessionStreamDelegate*
 & *URLSessionWebSocketDelegate* all inherit from *URLSessionTaskDelegate*

## Cache Policy

There are available different caching strategies governed by cache policies which
can help improve performance and reduce network traffic for application.

### URLSessionConfiguration requestCachePolicy

*Default value of requestCachePolicy is useProtocolCachePolicy*

This instance property for URLSessionConfiguration will determine when to return
a response from cache. As this property is for URLSessionConfiguration instance
hence it will affect the entire session, including how caching is handled globally 
for all requests made within that session.

So all requests made under session with some cache policy set using requestCachePolicy
on URLSessionConfiguration will get same cache policy unless a request uses it's
own policy which is covered below in URLRequest.

### URLRequest cachePolicy

Cache policy set at URLRequest will override the one defined in URLSessionConfiguration
so this comes in handy if for certain requests one want a different behaviour.

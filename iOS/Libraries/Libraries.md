#  Libraries

## Alamofire
https://github.com/Alamofire/Alamofire

Popular networking library which aims at simplifying networking tasks.
Builds on top of Apple's URL Loading System. Means underneath it is using URLSession and it's players.

APIs while using Alamofire now are called using *AF* like below :

```
AF.request("https://openlibrary.org/authors/OL1A.json").response { response in
            print("Received Response ::")
            print("\(String(data: response.data!, encoding: .utf8) as AnyObject)")
            completion()
        }
```

More examples at : [Examples](https://github.com/saurabh1088/uikit/blob/main/UIKitLearnings/UIKitLearnings/Networking/AlamofireNetworking/AlamofireNetworkingViewController.swift)

*AF* actually is defines as a reference to *Session.default*
```
public let AF = Session.default
```

## SDWebImage
https://github.com/SDWebImage/SDWebImage

Download images asynchronously with cache support.


## SwiftyJSON
https://github.com/SwiftyJSON/SwiftyJSON


## Realm
https://realm.io/

Alternative to SQLite


## Firebase
## SnapKit
## RxSwift
## AlamofireImage
## Kingfisher
## SVProgressHUD




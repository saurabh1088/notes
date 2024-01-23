# Persistence

Data Persistence refers to the longevity of data once the application which creates it is closed. In memory data remains
only for the time application is running and once application is killed, the in-memory data also goes away.
In order to achieve persisting data beyond application's runtime, data needs to be written to some non-volatile storage.

## Persistent vs Non-Persistent Data

## UserDefaults 

From Apple's official documentation of UserDefaults

*An interface to the user’s defaults database, where you store key-value pairs persistently across launches of your app.*

Source : https://developer.apple.com/documentation/foundation/userdefaults

- UserDefaults is as Apple states in official documentation is an interface to user's default database on device.
- UserDefaults are stored locally on device, except in case of managed devices in educational institutions.
- UserDefaults supports storing key-value pairs, where value can be of type NSData, NSString, NSNumber, NSDate, NSArray or
NSDictionary. Complex objects can be converted to NSData and saved.
- UserDefaults is Thread SAFE.

### What's the limit on data which can be stored in UserDefaults?

There is NO LIMIT on data which can be stored in UserDefaults EXCEPT for tvOS.

UserDefaults has a class/type property sizeLimitExceededNotification. This is a notification which gets posted once more
data is stored in user defaults than allowed.

For tvOS the size limit will post the notification when user defaults storage reaches 512kB in size. Also tvOS app will
get terminated if user defaults storage reaches 1MB in size.

sizeLimitExceededNotification is posted on the main queue.

## Plists



## SQLite

## Core Data

Core Data is a Framework provided by Apple to manage object graph.

Explore : https://github.com/saurabh1088/notes/blob/main/iOS/Persistence/CoreData.md

## Realm

Realm is an alternative to SQLite. It is backed by MongoDB.

It is/has:-
- fast
- lightweight
- scalable
- lazy loading
- zero-copy architecture
- Built-in mobile to cloud sync


## NSUbiquitousKeyValueStore

This is iCloud based container saving key-value pairs which are tied to iCloud account and enable access to data among
instances of user's apps running across connected devices.

## TODOs

1. Explore iCloud Storage and NSUbiquitousKeyValueStore



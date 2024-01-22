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

sizeLimitExceededNotification



## Plists

## SQLite

## Core Data

## Realm



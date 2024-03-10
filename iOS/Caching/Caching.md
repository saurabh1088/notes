#  Caching

## NSCache

Declaration as per official documentation :
```
class NSCache<KeyType, ObjectType> : NSObject where KeyType : AnyObject, ObjectType : AnyObject
```

Quoting definition from Apple's documentation page :

*A mutable collection you use to temporarily store transient key-value pairs that are subject to eviction when resources are low.*

NSCache is basically a NSMutableDictionary as NSCache also stored key value pairs like NSMutableDictionary, additionally
NSCache provides functionality to automatically evict objects to free up memory as required.


Source : https://developer.apple.com/documentation/foundation/nscache

### Transient

In Apple's official documentation, as per definition the mutable collection which is NSCache is *transient*.

Transient literally means lasting only for a short time OR impermanent. So this means that data stored in NSCache won't be
permanent but will be short lived. The reason for this is due to NSCache having certain *auto-eviction policies* in place.
These *auto-eviction policies* make sure that cache doesn't ends up using too much of system’s memory.

These auto-eviction policies will remove some data from cache if memory concerns arise.

### Thread Safety

While using NSCache, one can add, remove, and query items in cache from different threads without the need of locking the cache.

### Class restricted

Looking at declaration for NSCache it tell that both key and value are restricted to be of class types only. This restricts
usage of NSCache to class types only.

### Purgeable

The way NSCache allocates its memory it is purgeable, so NSCache performs better in memory-constrained environment.

## Caching and Memory

As discussed in link https://github.com/saurabh1088/notes/blob/main/iOS/Memory/Memory.md regarding memory compressor, that
how it will compress the memory which is not being accessed for a while, so that it can free up some memory. Now this can
have some complications while freeing up memory once an app receives memory warnings.

What complications?
Well, suppose an app is caching a bunch of data so that it can have better performance in not making network call again and
again to fetch that data. Now if the cache is left unused and gets compressed by the compressor, it can free up some memory.
Now app is not always a cause of memory warning, on a low memory device with bunch of other apps open can also trigger a
memory warning. So now our app with compressed cache receives a memory warning and as a part of handling memory warning the
app has implementation to remove all cache. Now since in order to remove all cache the cache ends up getting accessed and
it will cause compressor to decompress memory for it, so in a memory-contrained environment, the app actually went on to
use more memory.
So important thing to consider about caching is that one might use caching so as to prevent CPU from doing some task repeatedly,
but if one ends up caching too much, then it can result in memory issues.


## Benefits/Advantages of NSCache

NSCache is great for:
1. Performance
2. Auto-purging


## URLCache

- URLCache provides both in-memory and on-disk cache.
- One can manipulate size of in-memory and on-disk cache.
- One can control the path where cache data will be persisted.
- For iOS the on-disk cache can be purged when system runs low on disk space. However this will happen only when app is not running.
- URLCache is thread safe.


## How to decide between NSCache and URLCache?

NSCache and URLCache both cache data but they serve largely different purposes.
NSCache is great for performance, but it is in-memory only, so it will consume RAM. Using NSCache means one needs to be
carefull regarding memory warnings and also system can purge NSCache any time in case of low memory situations. One may
use NSCache but can also find it to be nil as system might have purged it. Also, being in-memory app termination will loose
data in NSCache.

URLCache serves the purpose of caching some data which usually one fetches over some network call. So the primary use case
here is to avoid network calls for data which doesn't changes too often hence can be cached. URLCache is both in-memory and
on-disk.

## TODOs

- [ ] URLSession cache
- [ ] NSDiscardableContent : Explore usage
- [ ] https://developer.apple.com/documentation/foundation/nsdiscardablecontent
- [ ] Try https://medium.com/@mshcheglov/reusable-image-cache-in-swift-9b90eb338e8d
- [ ] Try https://www.swiftbysundell.com/articles/caching-in-swift/

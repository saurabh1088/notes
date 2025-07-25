#  Caching


## 1. NSCache

Declaration as per official documentation :
```
class NSCache<KeyType, ObjectType> : NSObject where KeyType : AnyObject, ObjectType : AnyObject
```

Quoting definition from Apple's documentation page :

*A mutable collection you use to temporarily store transient key-value pairs that are subject to eviction when resources are low.*

NSCache is basically a NSMutableDictionary as NSCache also stores key value pairs like NSMutableDictionary, additionally
NSCache provides functionality to automatically evict objects to free up memory as required.


Source : https://developer.apple.com/documentation/foundation/nscache

### 1.1 Transient
In Apple's official documentation, as per definition the mutable collection which is NSCache is *transient*.

Transient literally means lasting only for a short time OR impermanent. So this means that data stored in NSCache won't be
permanent but will be short lived. The reason for this is due to NSCache having certain *auto-eviction policies* in place.
These *auto-eviction policies* make sure that cache doesn't ends up using too much of system’s memory.

These auto-eviction policies will remove some data from cache if memory concerns arise.

### 1.2 Thread Safety
While using NSCache, one can add, remove, and query items in cache from different threads without the need of locking the cache.

### 1.3 Class restricted
Looking at declaration for NSCache it tell that both key and value are restricted to be of class types only. This restricts
usage of NSCache to class types only.

### 1.4 Purgeable
The way NSCache allocates its memory it is purgeable, so NSCache performs better in memory-constrained environment.

### 1.5 In-memory cache
NSCache is an in-memory cache.

### 1.6 System is about to purge NSCache data, now what?
- In event when system is purging data from NSCache and one needs to take some action, one case use `NSCacheDelegate`.
- `cache(_:willEvictObject:)` will notify when object is being removed.

```
class MyCacheDelegate: NSObject, NSCacheDelegate {
    func cache(_ cache: NSCache<AnyObject, AnyObject>, willEvictObject obj: Any) {
        if let image = obj as? UIImage {
            print("NSCache is about to evict an image. You might want to save its identifier or perform other cleanup.")
            // Example: If you have a way to identify the image (e.g., its URL string),
            // you might log it or mark it as "needs re-download"
            // print("Evicted image data size: \(image.jpegData(compressionQuality: 0.8)?.count ?? 0) bytes")
        } else {
            print("NSCache is about to evict object: \(obj)")
        }
        // Here, you could save a key to a disk-based "recently evicted" list
        // if you want to prioritize re-downloading these items later.
    }
}
```

### 1.6 Benefits/Advantages of NSCache
NSCache is great for:
1. Performance
2. Auto-purging

### 1.7 Disadvantages of NSCache
1. In-memory only
2. It's volatile, meaning system will purge it in case of memory issues
3. No guaranteed order of eviction.
    - While generally LRU-like, there's no strict guarantee on which objects are evicted first.
4. Only supports class types.
5. Does not hold strong references to keys.
    - Keys are not retained, so if a key is deallocated elsewhere, its entry in the cache is removed.

## 2. Caching and Memory

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
So as `NSCache` is designed to be purgeable, it is better to rely more heavily on NSCache's auto-eviction policies (by
setting `totalCostLimit` and `countLimit` appropriately) and the `NSCacheDelegate`'s willEvictObject method for fine-grained
control, rather than a blanket `removeAllObjects()` in response to every memory warning.


## 4. URLCache

- URLCache provides both in-memory and on-disk cache.
- One can manipulate size of in-memory and on-disk cache.
- One can control the path where cache data will be persisted.
- For iOS the on-disk cache can be purged when system runs low on disk space. However this will happen only when app is not running.
- URLCache is thread safe.


## 5. How to decide between NSCache and URLCache?

NSCache and URLCache both cache data but they serve largely different purposes.
NSCache is great for performance, but it is in-memory only, so it will consume RAM. Using NSCache means one needs to be
carefull regarding memory warnings and also system can purge NSCache any time in case of low memory situations. One may
use NSCache but can also find it to be nil as system might have purged it. Also, being in-memory app termination will loose
data in NSCache.

URLCache serves the purpose of caching some data which usually one fetches over some network call. So the primary use case
here is to avoid network calls for data which doesn't changes too often hence can be cached. URLCache is both in-memory and
on-disk.


## 6. URLSession and cache

Using URL Loading System one can set cache policies to govern if and how to cache request's responses. There are following
ways to set a cache policy while using URLSession.

1. *URLSessionConfiguration* has instance property *requestCachePolicy*, setting this impacts all the requests in the session
configured with configuration object.

2. *URLRequest* has instance property *cachePolicy*, this impacts the particular request only for which it is being set
and will override if any cache policy was set at *URLSessionConfiguration* level.

*URLSessionConfiguration* has instance property *urlCache* of type *URLCache*. This implies URLSession using URLCache for
caching duty.


## 7. TODOs

- [ ] URLSession cache
- [ ] NSDiscardableContent : Explore usage
- [ ] https://developer.apple.com/documentation/foundation/nsdiscardablecontent
- [ ] Try https://medium.com/@mshcheglov/reusable-image-cache-in-swift-9b90eb338e8d
- [ ] Try https://www.swiftbysundell.com/articles/caching-in-swift/
- [ ] Good read https://medium.nextlevelswift.com/urlrequest-cache-policy-f7c30a96b698


#  Caching

## NSCache

Declaration as per official documentation :
```
class NSCache<KeyType, ObjectType> : NSObject where KeyType : AnyObject, ObjectType : AnyObject
```

Quoting definition from Apple's documentation page :

*A mutable collection you use to temporarily store transient key-value pairs that are subject to eviction when resources are low.*


Source : https://developer.apple.com/documentation/foundation/nscache

### Transient

In Apple's official documentation, as per definition the mutable collection which
is NSCache is *transient*.

Transient literally means lasting only for a short time OR impermanent. So this means
that data stored in NSCache won't be permanent but will be short lived. The reason
for this is due to NSCache having certain *auto-eviction policies* in place.
These *auto-eviction policies* make sure that cache doesn't ends up using too much 
of system’s memory.

These auto-eviction policies will remove some data from cache if memory concerns
arise.

### Thread Safety

While using NSCache, one can add, remove, and query items in cache from different
threads without the need of locking the cache.

### Class restricted

Looking at declaration for NSCache it tell that both key and value are restricted
to be of class types only. This restricts usage of NSCache to class types only.

### Purgeable

The way NSCache allocates its memory it is purgeable, so NSCache performs better in memory-constrained environment.


## TODOs

1. NSDiscardableContent : Explore usage
- https://developer.apple.com/documentation/foundation/nsdiscardablecontent

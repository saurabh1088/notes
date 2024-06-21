#  Swift Noncopyable


## Source
Consume noncopyable types in Swift
https://developer.apple.com/videos/play/wwdc2024/10170/


## What is Copyable?
- Copyable is a new protocol in Swift.
- This protocol describes the ability for a type to be automatically copied.
- The protocol doesn’t have any member requirements.
- Everything in Swift is inferred to be copyable by default.
- Swift assumes, one need the ability to copy.


## How to define something as noncopyable?
`~Copyable`

```
struct SomeNonCopyableType: ~Copyable { }
```

- Using `~Copyable` will suppress the auto-conformance to `Copyable` protocol.
- When one try to copy a noncopyable type, then Swift will consume instead of copy. For example

```
let object1 = SomeNonCopyableType()
let object2 = consume object1
```

`consume` is not required to be written here explicitly, but can be written for clarity.
Consuming a variable takes its value, leaving the variable uninitialised.

## TODO
- [ ] Complete this topic
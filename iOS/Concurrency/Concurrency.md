# Concurrency

`GCD` and `OperationQueue` are two ways one can implement concurrency in iOS/macOS development.

## 1. GCD

## 2. Operations


## 3. When to choose Operations over GCD?
Operations can have advantages over GCD based on the scenario at hand. Below discussion points out several of those
scenarios one may face in application leading to Operations forming a better choice.

1. Complex Dependency Management
When demand is to perform a series of tasks with complex dependencies between those, then GCD doesn't serves the purpose
and one need to utilize operations to establish required dependencies.

For example:
An app needs to download images and then before showing those on user interface, need to process the images. Here one can
say there are three operations to perform.
- image download operation
- image processing operation
- user interface updates with images operation

Dependencies while working with `OperationQueue` can also be added to `Operation` being executed on different `OperationQueue`'s. Check example at link below
https://github.com/saurabh1088/swift-playgrounds/blob/main/Concurrency.playground/Pages/OperationQueues.xcplaygroundpage/Contents.swift


2. Re-usability
`Operation` is an abstract class, hence can't be used directly. There are some implementations available ready to use from
standar library like `NSInvocationOperation` or `BlockOperation`. However one can subclass `Operation` and implement any
custom operation if required. This also helps in re-usability.


3. Observability
Operation provide several KVO complaint properties which can be observed to understand the state of operation.


4. Task priority
TODO: Check on this in comparison to GCD.


5. Pause and resume tasks


6. Completion block for tasks
Each `Operation` added to `OperationQueue` can have a completion block defined, which gets executed once that `Operation` gets
completed. This is great if one needs to execute some logic on completion of individual Operations.


8. Maximum concurrent operation limit
`OperationQueue` has property `maxConcurrentOperationCount` which can be used to set maximum number of concurrent operations
the queue can perform. For example, setting it to 1 causes queue to perform each operation one by one.


## 4. Actors

### 4.1 What are Actors?
- Primary goal of actors is to prevent data races and ensure safe access to shared mutable state in concurrent programming.
- Conceptually Swift actors are classes as actors also are reference type.
- Major difference wrt classes is that actors don't participate in inheritance.
- Actors are safe to use in concurrent environment.
- Swift automatically ensures no attempt is made to access an actor's data simultaneously, this is at compile time itself
without the need for developers to write boilerplate code using locks.
- While using an actors mutable state from outside of actor or from another actor, one would need to use await calls.
- Behind the scenes actors can be thought of operating a private queue and taking request one at a time. If no requests are
there access to mutable state may be fulfilled straight away, else it can take time, hence the usage of await.
- For a constant property defined in an actor, await is not required when accessing it, as the constant property isn't
a mutable one and doesn't needs isolated access.
- Methods in actors are isolated by default.
- If method is not accessing any mutable data, then it is good practice to mark it as nonisolated.
- nonisolated can be used for computed properties as well of those aren't being computed of any mutable state.

### 4.3 Actors and isolation
In Swift, when we say that actors guarantee data isolation, we mean that all mutable properties and functions within an
actor are isolated from direct access from the outside. This isolation is a core feature of actors and is crucial for
ensuring thread safety in concurrent programming.

### 4.3 Can one use nonisolated on a let constant property in an actor as those are non mutable?
YES, one can declare a let constant property as nonisolated in an actor.
Refer example at below playground:
- https://github.com/saurabh1088/swift-playgrounds/blob/main/Concurrency.playground/Pages/Actors.xcplaygroundpage/Contents.swift

When one encapsulates data within an actor, one is essentially isolating it from direct access by other parts of the
program. Any code that wants to interact with the data must go through the actor, effectively ‘lining up’ and waiting
its turn. This means that even in a concurrent environment, the actor serializes access to its data, ensuring that only
one piece of code interacts with it at any given time.


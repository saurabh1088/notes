# Concurrency

`GCD` and `OperationQueue` are two ways once can implement concurrency in iOS/macOS development.

## GCD

## Operations


## When to choose Operations over GCD?
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
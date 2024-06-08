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

2. Cancellable tasks
If one needs to perform some task, which is desired to be cancelled under certain conditions, then one need to use operations
as GCD doesn't have provision to cancel a task once dispatched.
In GCD's `DispatchWorkItem` there is an instance method `cancel()`. This cancels any future attempts to execute the work
item, calling this doesn't affect the execution of work item which is already in progress.

3. Re-usability
`Operation` is an abstract class, hence can't be used directly. There are some implementations available ready to use from
standar library like `NSInvocationOperation` or `BlockOperation`. However one can subclass `Operation` and implement any
custom operation if required. This also helps in re-usability.

4. Observability
Operation provide several KVO complaint properties which can be observed to understand the state of operation.

5. Task priority
TODO: Check on this in comparison to GCD.
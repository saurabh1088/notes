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
An app needs to download images and then before showing on ui, need to process the images. Here one can say there are three
operations to perform.
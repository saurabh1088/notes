# Swift Performance

wwdc video : https://developer.apple.com/videos/play/wwdc2016/416/

wwdc video : https://developer.apple.com/videos/play/wwdc2016/419
Protocol and Value Oriented Programming in UIKit Apps

## Local Reasoning

## How value types and protocols can make app better.
Code should be such that, when one looks at it, it is understandable without need to think about how it interacts with
rest of the code. This makes code easier to maintain, test and easier to write. When code is structured using Inheritance
then this problem arises, as inheriting from parent, while implementing one need to think about what parent has implemented
and what further child classes will inherit, so one has to think a lot about whole lot of code around that.

The answer to Inheritance is Composition. Composition is a very simple idea of combining smaller pices together to build
larger pieces.

1. Model layer should be value types.
2. Use composition for Views, using Generics and Protocols
3. Controllers should have a single model property instead of multiple properties wherever possible, also use enums for
managing mutually exclusive ui states.

## Generic Types
Using generic types have advantage as using generic types:
- Gives more control over types
- Compiler has more information about what code is doing hence it can optimize more

## Class vs Struct
Class instances are expensive. 

## Case of UIView in UIKit vs View in SwiftUI
One uses composition while creating views. Which is to say a view is often composed of several views arranged in a view
hierarchy. Now in UIKit we have UIView, which is a class. Class instances are expensive. Creating objects of classes adds
allocations over heap memory which gets worse for views. There is a ton of work which is needed to support a view so as to
allow it do things like drawing and event handling. This is the reason one tries hard to minimize number of views.

With Swift, struct was introduced with value semantics. It is much better to perform composition using value types. Structs
are very lightweight and are not associated with heavy cost associated with classes. In SwiftUI View is actually a protocol.
A SwiftUI view need to implement protocol View and all SwiftUI views are structs.

## How to narrow down design space?
Swift as a modern programming language offers a bunch of features at one's disposal to write some amazing code. But as a
developer one need to narrow down on these features and pick the most suited to solve a piece of puzzle/problem or implement
something new. So how does one narrow down the choices. Well one can narrow down based on:
1. Modelling
    - This could be if to follow value or reference semantics, or to use protocols or inheritance etc.
2. Performance

## Dimensions of Performance
While builting a software application one need to decide upon the abstraction mechanism. For example should one use classes
or structures, or should one go for protocols or inheritance. While deciding upon these abstraction mechanisms one should
as questions like

1. Do we need stack allocation of heap for instances
2. What will be the reference counting overhead is going to occue
3. When a method is called on an instance then should it makes sense to statically or dynamically dispatched.

So from three points above the dimensions like stack/heap, reference counting, static/dynamic disptach are dimentions and
the decision to choose abstraction mechanism often comes out of how one can trade off between these dimensions for better
performance.

## Dimenstion of Performance : Allocation
Allocation and deallocation of memory in Swift is done automatically and some of the memory is allocated on stack. Stack
is a region of memory which works in LIFO manner. One can push an item onto stack or pop an item out. It is a very simple
and straightforward data structure. The push and pop operations on stack are only ever going to be performed at the end
of the stack, so all needed is a pointer to the end of the stack. Allocating and deallocating from stack is simple matter
of incrementing or decrementing the stack pointer which points to the end of stack. So all this means that stack allocation
is very fast. It is almost as fast as literally assigning the cost of an integer.

Now Heap is dynamic and much more advanced data structure. Allocating something on heap means one has to traverse through
it to find a free block of memory of appropriate size and then allocating. Then also deallocating once done. This means there
is more work involved and it is more complex than stack allocation. Also there is an aspect that there might be multiple
thread running which are allocating memory to heap at same time, so the heap data structure also need to take care of maintaining
its integrity and implement some locking or synchronization mechanism. This makes it more complex and makes dealing with
heap at the large cost.

So being careful about when and where one is allocating memory to heap, one can drastically improve performance of the app.

Now in Swift we have Struct and Classes. Classes require heap allocation. When we use classes the references are allocated
on stack, but the actual memory is allocated on heap. This implicates:
*Classes are more expensive to construct than structs as classes need heap allocation.*
So unless there is a case for using classes, one should be better off with using structs.

## Dimenstion of Performance : Reference Counting
There is also a cost associated with reference counting when dealing with reference types. Reference counting is frequent
operation and it has to be atomic operation in a multi-threaded environment. Hence the cost involved is huge.

String in Swift stores the contents of it's cahracters on Heap. So when dealing with String if one can instead opt for a
struct one should do so.

## Dimenstion of Performance : Method Dispatch
When a method is called, then at runtime Swift will need to make sure to execute the correct implementation. If this implementation
can be determined at compile time itself then it's *static dispatch*
In *dynamic dispatch* the compiler is not having visibility for which method implementation to call, it is going to be decided
at runtime. Now this is only adding some additional redirection at runtime and not some hude performance cost increment.
But compiler won't be able to optimize code in dynamic dispatch scenario and perform *inlining*
Now compiler has a full view of a chain of static dispatches, which is not viable in case of chain of dynamic dispatches.

So classes results in dynamic dispatch by default, so this doesn't causes immediate increase in cost on performance but when
there is chain of calls involved it will prevent compiler from doing optimizations like inlining and this can add up and make
performance issues.

Now not all classes will require dynamic dispatch. If there is a class which is supposed to be never subclasses then it should
be marked as final, for final class compiler will dispatch it's method statically.

## Polymorphism using Protocol Oriented Programming
Polymorphism without inheritance and reference semantics

In example method `examplePolymorphismUsingProtocols` below the `myGarage` array can hold any type which conforms to `Vehicle` 
protocol, so basically `myGarage` can hold any `Vehicle`, but these `Vehicle` types don't share any common ancestor, which
is there is no common inheritance relationship here. So here there is no `V-Table` dispatch happening. Instead here the
mechanism used will be `Protocol Witness Table`.

```
swift
protocol Vehicle {
    func drive()
}

struct Car: Vehicle {
    func drive() {
        print("Driving a Car 🚗")
    }
}

struct Bike: Vehicle {
    func drive() {
        print("Driving a Bike 🏍️")
    }
}

func examplePolymorphismUsingProtocols() {
    var myGarage = [Vehicle]()
    myGarage.append(Car())
    myGarage.append(Bike())
    for vehicle in myGarage {
        vehicle.drive()
    }
}
```
Check example : https://github.com/saurabh1088/swift-playgrounds/blob/main/Swift.playground/Pages/Protocols.xcplaygroundpage/Contents.swift

### Protocol Witness Table
Protocol Witness Table is a table based mechanism which helps in method dispatch in protocol oriented programming. Normally
in inheritance using reference types there is a concept of V-Table dispatch. But when one designs using protocols then conforming
types are not related via any parent, so there method dispatch is done via Protocol Witness Table.

*So a Protocol Witness Table is a dynamic dispatch without V-Table*

Every type which implements the protocol gets a Protocol Witness Table. Entries in this Protocol Witness Table link to an
implementation in the type.

**Existential Container**
An array storing types which conform to protocols can have elements stored of unrelated types and of different memory needs.
How Swift will decide to allocate memory while storing in Array? Well Swift uses a special storage layout which is called
Existential Container. Some initial space/words are reserved in Existential Container for value buffer. Types not requiring
enought memory needs can fit into this value buffer. When memory requirement is large then Swift will allocate memory on heap
and store reference on value buffer.

An Existential Container contains:
1. Inline Value Buffer: 3 words
2. Reference to large values stored on Heap
3. Reference to Value Witness Table
4. Reference to Protocol Witness Table

### Value Witness Table
The Value Witness Table manages the lifetime of value and there is one of those tables per type in a program. The Existential Container
discussed above has a referece to the Value Witness Table. Also the Existential Container contains reference to the Protocol Witness Table.

## TODOs
- [ ] Add example using code.
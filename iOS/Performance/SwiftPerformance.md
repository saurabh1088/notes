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

# Swift Performance

wwdc video : https://developer.apple.com/videos/play/wwdc2016/416/

wwdc video : https://developer.apple.com/videos/play/wwdc2016/419
Protocol and Value Oriented Programming in UIKit Apps

## How value types and protocols can make app better.
Code should be such that, when one looks at it, it is understandable without need to think about how it interacts with
rest of the code. This makes code easier to maintain, test and easier to write. When code is structured using Inheritance
then this problem arises, as inheriting from parent, while implementing one need to think about what parent has implemented
and what further child classes will inherit, so one has to think a lot about whole lot of code around that.

The answer to Inheritance is Composition. Composition is a very simple idea of combining smaller pices together to build
larger pieces.

1. Model layer should be value types.

# OOPS in Swift

## Abstraction
Abstraction separates ideas from specific details.

Different ways to achieve abstraction:

### 1. Functions & Methods
This is a general way of achieving abstraction by extracting some functionality into a function or method. What abstracting some functionality to a function gives is to express idea of what is happening without giving away the implementation details
or repeating the details.

### 2. Protocols
A protocol is an abstraction tool that describes the functionality of conforming types.
Using a protocol, one can separate the ideas about what a type does from the implementation details.
The idea is expressed through the protocol, however the implementation is separate.
Protocols are a language construct which are designed to represent capabilities of types without the details of how the
capability works.

### 3. Generics
Generics are a fundamental tool for writing abstract code in Swift. Using Generic code one can abstract away the concrete
types. If we have a set of types which are all the same idea with different details, one can write abstract code to work
with all of those concrete types.

## Encapsulation
Literal meaning : *The process of expressing or showing the most important facts about something*

Encapsulation by definition means bundling of data and methods which operate on data in a single unit.

### How to achive encapsulation in Swift
1. Structs and Classes
2. Access modifiers


## Inheritance

## Polymorphism
The ability of abstract code to behave differently for different concrete types is called *Polymorphism*. Polymorphism
allows one piece of code to have many behaviors depending on how the code is used.

Polymorphism can be achived via:

### 1. Function Overloading
Overloading achieves an ad-hoc Polymorphism because it isn't a general solution. Overloading leads to repetetive code. This
will force to use reference semantics.

### 2. Function overriding
This achieves subtype Polymorphism. Here the subtype(subclass) can have a different behaviour. If a function is implemented
by different subtypes then how it behaves will depend upon which subtype the function is called at runtime.

Types of Polymorphism:

1. Ad-hoc Polymorphism
    For example: Operator + can add integers as well as concatenate strings.

2. Subtype Polymorphism


3. Parametric Polymorphism
    For example: Generics in Swift, where a piece of code is allowed to be typed generically instead of actual types.

TODO: Move this to some proper place
## WWDC https://developer.apple.com/videos/play/wwdc2022/110353 Design protocol interfaces in Swift

The strategy of using the same representation for different concrete types is called type erasure.

When one calls a method returning an associated type on an existential type, the compiler will use type erasure to determine
the result type of the call. Type erasure replaces these associated types with corresponding existential types that have
equivalent constraints.

Type erasure does not allow us to work with associated types in consuming position. Instead, one must unbox the existential
*any* type by passing it to a function that takes an opaque *some* type.

Constrained opaque result types.


## TODOs
- [ ] Opaque types must always be named for generic types. Make a Opaque types TOPIC.
- [ ] Watch https://developer.apple.com/videos/play/wwdc2022/110353
- [ ] What is a lazy collection : LazyFilterSequence
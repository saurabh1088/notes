#  Swift

## Swift open source update

- swift.org/swift-evolution All language proposal
- Vision documents apple/swift-evolution/visions. Logic behind vision is that 
some of the enhancements in Swift has been due to combination of multiple proposals 
forming a larger feature itself. To drive this comes vision documents. First 
enhanement to come out of vision is Swift Macros.
- Ecosystem steering group, parallel to language steering group

## Expressive Code
- if else and switch statements are now allowed to be used as expressions

- Result builders
- Faster type checking
- Improved code completion
- More accurate error message
    - This improvement was particularly focused on invalid code. Previously result 
    builder code with errors would take a long time to fail, as the type checker 
    would explore the many possibilities for valid paths. Now invalid code type 
    checks much faster. Also previously error used to come in an completely unrelated 
    part of the result builder, now it’s more accurate.

- Generic system in Swift 5.9 is gaining first class support. Previously multiple 
overloaded methods would be required if requirement is to take multiple arguments 
and return multiple values. 
- Type parameter pack.
- Using type parameter pack, APIs which have multiple overloads can be collapsed 
down into a single function.

TODO: Watch : Generalize APIs using parameter pack

## Macros

- Eliminating boilerplate and unlocking more
- Macros are distributed as packages
- macro keyword
- Most macros are defined as #externalMacro
- External macros are defined in separate programs which act as compiler plugins. 
- Swift compiler passes the source code for the use of the macro to the plugin, the 
plugin will produce a new source code which then is integrated back to Swift program
- Expanded source code is right there in Xcode editor and one can also put debugger 
into it


## Swift everywhere

- Swift is highly efficient, it compiles natively and Swift’s use of value types 
and of reference counting instead of garbage collection means it’s able to achieve 
a low memory footprint. This scalability means we are able to push Swift to more 
places than was previously possible with Objective-C, to low level systems where 
previously one might have to use C or C++

- Open sourced start of re-write of the Foundation framework in Swift which will 
lead to a single shared implementation of Foundation on both Apple and non-Apple 
platforms.

- Foundation initiative need re-writing whole lot of Objective C code in Swift. 
In iOS 17 and macOS Sonoma there are new Swift backed implementations of essential 
types like Date and Calendar

- Calendar calculations 20% faster (Due to Swift’s value semantics)

- Date formatting 150% faster

- JSON coding 200-500% faster

- New opt-in features to achieve a new level of control.

- One can make a struct non copyable like below, this also allows to provide a deinit
in struct

```swift
struct NonCopyableStruct: ~Copyable {

}
```

## C++ interoperability

Many codes not just have Swift and Objective C code both interoperating, but also
have some core business logic implemented in C++.

Swift 5.9 introduces ability to interact with C++ types and functions directly from
Swift.

C++ can directly use most of Swift types and their full APIs without using any attribute
like @objc which is required for Swift and Objective C interoperability.

Support for Swift in CMake.


## Abstract concurrency model

Abstract model has two main pieces:-
- Tasks 
    Tasks are sequential unit of work which can be run anywhere, can be suspended
- Actors
    Actors are a synchronization mechanism that provide mutually exclusive access 
    to isolated state

#  TypeScript

TypeScript extends JavaScript syntax and adds strong typing to it.
One need to compile TypeScript code into JavaScript code before it can be run on
a JavaScript environment like browser or Node.js

File extension of a TypeScript file is .ts

For e.g. below is a valid JavaScript code and it won't cause any issues. However
this will not work with TypeScript.

```
let name = "Batman";
name = 120
```

### transpile

*Transpiling converts source code from a programming language into an equivalent
source code of the same or a different programming language.*

When one uses TypeScript in code, one usually writes code in files with *.ts* extension
and then these files are compiled with a TypeScript compiler which transpiles these
to JavaScript. Resulting JavaScript code can be run in any JavaScript environment
i.e. either browser or Node.js


### TypeScript Basic types

- number
- string
- boolean

### TypeScript other types

- Array (Yes, it's with a uppercase A, and not array unlike number, string and boolean types)
- any
- undefined
- null
- never (represents a type for functions that never return)
- void (represents type for function which doesn't returns anything, undefined can also be used but void is better)

### Types union : union type

In TypeScript one can have a union of types if the requirement is such to use
multiple types for example :

```
Here we are telling that variable can either be a string or a number

let variable: string | number = 'some value';
variable = 100;
```

## Features TypeScript adds on top of JavaScript

### Static Typing

JavaScript is not a static typed language. TypeScript adds static typing to JavaScript.
This addition enables writing code for JavaScript which is having all type safety
right at the compile time itself thereby preventing several runtime issues.

### Interfaces

TypeScript adds interfaces to JavaScript. Interfaces helps one define objects. This
enforcing objects conforming to a specific structure.

### Enums

Enums are a great way to club well named defined constants providing type safety.

### Union and Intersection types

One can define a type in typescript using a union of differnt types for example.

```
Here we are telling that variable can either be a string or a number

let variable: string | number = 'some value';
variable = 100;
```

### Generics

TypeScript enables capability of *generic* types such that functions or classes
can work with differnt data types without need to re-declare those with each required
types.

### Type Inference

There is no need to explicitly provide type while declaring a variable if the initial
value is provided while declaration itself, the TypeScript can infer type based
on value which is assigned.

### Advanced Function Types

### Namespace and Module Support

TypeScript provides a module system to organize code into reusable components.
Namespaces and modules help avoid naming conflicts and manage code dependencies.

### Decorators

### Declaration Files


## type vs interface

Both *type* and *interface* are keywords in TypeScript which can help to define
the structure of objects, however there are some differences

|type|interface|
|---|---|
|It's kind of an alias, like typealias in Swift|It's used to declare a named set|
|No declaration merging|Declaration merging is possible|
|Classes can't implement type|Classes can implement interface|
|-|interfaces can extend other interface|


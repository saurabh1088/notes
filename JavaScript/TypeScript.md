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

### Types union : union type

In TypeScript one can have a union of types if the requirement is such to use
multiple types for example :

```
Here we are telling that variable can either be a string or a number

let variable: string | number = 'some value';
variable = 100;
```


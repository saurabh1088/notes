#  JavaScript

Initially JavaScript used to be interpreted language, as when web browsers used
to come across JavaScript, they used to interpret it line by line and execute it
on the fly.

## Just In Time Compilation

Nowadays we have JavaScript engines like :
- V8 in Chrome
- SpiderMonkey in Firefox
- JavaScriptCore in Safari

These modern JavaScript engines employ a just-in-time (JIT) compilation process.
When code is compiled, then compiler converts source code into machine code and then
the generated machine code is executed. This process makes execution fast but startups
are slow due to time it takes for compilation.
Startup time is fast with interpreted languages as there the code is simply translated
and executed line by line. Problem with interpretation is that for any code which
lets say is getting repeated multiple times for example say in a loop then this
whole interpretation is going again and again which becomes inefficient.

Just In Time Compilation aims to fix this interpreter’s inefficiency. JITs will
have a monitor or profiler which while code is getting executed by the interpreter
will keep track of how many times the different statements get hit. This way it
will detect parts of code being used most and those can be compiled and stored.

JavaScript however is still considered an interpreted language, since the compilation 
is handled at run time, rather than ahead of time.


JavaScript
- lightweight
- interpreted or just in time compiled
- first-class functions
- prototype-based
- multi-paradigm
- single-threaded
- dynamic language
- object-oriented
- imperative and declarative
- dynamically typed

On a web browser, each tab is having it's own environment for execution. This means
usually the code in each tab run completely independent of each other. This is good
from security point of view. There are however ways to safely send code and data 
between different websites/tabs

## Adding JavaScript to HTML

### Internal JavaScript

```
<script>
  // Internal JavaScript code comes here
</script>
```

### External JavaScript

Internal JavaScript option works fine, but is not a great way to manage code. It's
a lot better to have JavaScript code live outside of HTML files with only reference
to the actual file from HTML.

```
<script src="externalJavaScript.js"></script>
```

### Inline JavaScript handlers

One can also have JavaScript literally living inside HTML. However this is BAD PRACTICE,
and should be AVOIDED.

```
<button onclick="buttonClickHandler()">Click me!</button>
```

## Script loading strategies in JavaScript

Webpages are loaded with HTML from top.


## async and defer


## JavaScript Objects

To create an object in JavaScript one can simply declare like below. This is creating
object using object literal. This is the easiest approach and one can both define
and create object in single line.

```
This will create an empty object employee
const employee = {}
```

```
const employee = {name: "Batman", employeeId: 1}
```

Another approach is to use *new Object()*

```
const employee = new Object()
employee.name = "Batman"
employee.employeeId = 1
```

Accessing the property can be done using dot notation and also using a bracket
notation.

```
console.log(employee.name)
console.log(employee["name"])
```


## JavaScript Object prototypes

Prototypes is a mechanism in JavaScript through which JavaScript objects inherit
properties and methods from other objects. 

Every object in JavaScript has a built in property i.e. *prototype*. This prototype
is basically a reference to another object which will have it's own *prototype*.
This creates a chain till the point when an object is reached which is having *null*
as it's *prototype*.

When a property or method is accessed on an object, JavaScript looks for it in
the object itself. If it doesn't find it, it looks in the object's prototype, and
so on, until it finds the property/method or reaches the end of the chain.

This *prototype* property for an object is not called prototype, all browsers use
*__proto__*. Usage of *__proto__* is discouraged as per official documentation.
Source : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/proto

Standard way to access an object's prototype is *Object.getPrototypeOf()* method.

### Setting a prototype

Prototype for an object in JavaScript can be set while creating the object using
*Object.create()* method.


```
const employee = {name: "Batman", powers() { console.log("Because I'am Batman")}}

Create a prototype of employee which will inherit all from it.
const employeePrototype = Object.create(employee)

console.log(employee.powers)
console.log(employeePrototype.powers())

Both will print "Because I'am Batman"
```

In the example above an object *employee* was defined and then a prototype was
created using it. The prototype object created *employeePrototype* inherits all
properties and methods defined from object it was created.

One can get the prototype of *employeePrototype* like below, note however *__proto__*
is NOT recommended.

```
NOT RECOMMENDED
console.log(employeePrototype.__proto__)

RECOMMENDED
console.log(Object. getPrototypeOf(employeePrototype))
```

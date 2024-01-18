#  JavaScript

JavaScript is a scripting or programming language allowing one to implement complex
featured for a web page.

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

Webpages are loaded with HTML from top. There may happen issues wherein a JavaScript
loads and executed before the HTML content loads on which the JavaScript was expected
to perform some DOM manipulatiions, in this case it will give error.
One way to overcome this is to take help of event listener `DOMContentLoaded`

`DOMContentLoaded` is an event which signifies that HTML body is completely loaded
and parsed. One can put JavaScript logic manipulating DOM under this event check
so as to run only when HTML is completely loaded.


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

JavaScript is a prototype-based language
JavaScript follows Prototype-Based Inheritance

### Classes in JavaScript

Classes in JavaScript were introduced from ES6. With introduction of class keyword,
JavaScript also got a traditional class-based way of creating objects. This introduction
enabled a more convenient way to create a constructors and work with prototypes.

JavaScript's inheritance model still remains prototype-based, even after introduction
of class keyword.

*class* in JavaScript is actually a syntactic sugar over the existing prototype
based system.

So basically class keyword provides a more familiar and clean syntax for creating
objects and their methods, but under the hood, it still uses prototypes to link
objects and inherit properties and methods.


## Asynchronous JavaScript

JavaScript is single-threaded. This implicated it will only execute one thing at
a time. It has only one execution thread in it's runtime environment (be it browser
or Node.js).

This single thread in JavaScript is hence responsible for lot of things :
- Executing code
- Event handling
- DOM handling

Now in order to support tasks which can be potentially long running, synchronous
operations for those wouldn't make sense. Luckily JavaScript supports asynchronous
programming which allows those operations to be executed asynchronously without
blocking and achieving concurrent like behaviour.

Note however asynchronous tasks in JavaScript won't be creating any additional thread,
instead an event loop within the main thread itself will handle those operations
efficiently.

## JavaScript declare variables/constants

### const, let and var

*let* is used in JavaScript to declare a variable (unlike Swift where let is used
to declare a constant)

```
let someVariable = "some value";
someVariable = "some other value";
```

*var* is another way to declare a variable in JavaScript. So basically one can
declare a variable in JavaScript using *let* OR *var* (Contrast this with Swift
where *let* declares a constant and *var* a variable)

### About let and var

When JavaScript was created *var* was only way to declare variables. Due to issues
with few aspects of *var*, *let* was introduced in modern JavaScript to erase the
issues with *var*. Few difference in these two are :

- With *var* in a multiline JavaScript program one can actually declare a variable
with *var* after it's initialized and code will work just fine. This happens due
to *Hoisting*

- With *var* redeclaration is possible

What is hoisting?
*Hoisting* in JavaScript is a process via which interpreter appears to move
declarations of functions, variables etc to the top of their scope before execution.
Declaration anywhere in code is equivalent to declaring right at top, hence it also
means that the variable can appear to be used before being declared itself.

This code is completely valid and won't give any issues, provided one is not executing
this line by line in console.

```
someVar = "value";
var someVar;
```

However one important point to be noted is that only the declaration is hoiseted
but not the initialization so below code will give error

```
console.log(someVar); // undefined
var someVar = "value";
```

Should one use *var* now?

Features supported by *var* like hoisting and redeclaration are confusing. Hence
it is advisable to use *let* instead, there is no reason in using *var* now as all
modern browsers support *let*.

### const

*const* in JavaScript is used to create constants, these need to be initialized
while declaration itself and can't be assigned new value post that.

However if *const* is refering to an object, then the object itself can be updated.
Note that only object properties can be updated, being declared a const, the const
can't be assigned a new object.

```
const someObject = { name: "Batman" };
someObject.name = "Superman";
```

## JavaScript Events

JavaScript Events are actions happening in browser in response to user interactions
or possibly some other events.

An Event can be :
- a button clicked
- a page loading
- a video playing
- cursor moved
etc.

There are Event listeners which observes events and call event handlers. Event handlers
are blocks of code running in response to event firing.


Example below shows how to use event handler in HTML
```
<button onclick="buttonTapped()">Click me</button>

function buttonTapped() {
  alert("Button tapped!");
}
```

However a better practice is to use like below, using this way the code is all in
JavaScript file and HTML is seperated leading to flexibility and separation of concern.
```
var button = document.getElementById("someButton");

button.addEventListener("click", function() {
  alert("Button tapped!");
});
```

## Number

Unlike other programming languages having different types for integer and decimal
types, for example Swift has Int, Float, Double etc, JavaScript has single data 
type i.e. *Number*

```
var someInteger = 1;
var someFloat = 2.5;
typeof someInteger; // prints 'number'
typeof someFloat; // prints 'number'
```

## Strings

### Single quotes, double quotes, and backticks

Strings can be declared in JavaScript using single quotes, double quotes or backticks.
Using single quotes OR double quotes is same.

String declared using backticks are a special kind of strings. These strings are
called *template literal* and these have some special properties.

Using *template literal* one can :
- embed JavaScript in these strings
- declare multiple lines


## Arrays

JavaScript arrays can contain multiple data types in a single array like below.

```
const someArray = ["batman", 1, 2.5, "Gotham"]
```

## Functions

In JavaScript one uses *function* keyword to define a function.

Functions in JavaScript are *hoisted*, this means irrespective of where those are
declared those are hoisted and moved to the top of scope. for example below a function
someFunction is defined, however it is used before the declaration starts, but due
to it being hoisted there won't be any issues with this code.

```
someFunction();

function someFunction() {
  console.log('Function is hoisted!');
}
```

### Anonymous functions

Anonymous function in JavaScript are function which are defined without any names.
Mostly the use-case of anonymous functions is for certain short lived operations
or passing as arguments to other functions.

Below is example of declaring anonymous function. This way is also called as
*function expression*.
*Function expressions are not Hoisted*
```
(function () {
  alert("This is an anonymous function");
});
```

Functions can also be assigned to variables, so one can declare a anonymous function
and assign it to some variable like below:

```
var someAnonymousFunction = (function () {
  alert("This is an anonymous function");
});

This will be called like below :
someAnonymousFunction()
```

When passing a funtion to another function 

```
function someFunctionWithCallback(callback) {
    console.log("This is a function which takes another function as argument");
    callback();
}


Option 1
One way is to define a function and pass it
function callbackFunction() {
    console.log("I am a function passed to another function")
}

someFunctionWithCallback(callbackFunction)


Option 2
Calling using anonymous function syntax
someFunctionWithCallback(function() {
    console.log("I am a function passed to another function")
});


Option 3
If option 2 is used, then there is another syntax which is available which is called
as Arrow functions
someFunctionWithCallback(() => {
    console.log("I am a function passed to another function using arrow function syntax")
});
```

## <script src="externalJavaScript.js"> : <head> vs <body>

IMP : Does it makes a difference if external JavaScript is added via <script> tag
is added in <head> vs <body>?

One can place an enternal JavaScript file reference using <script> tag with src
inside HTML document either in <head> or in <body>. Both options can work depending
upon scenarios.

### <script src="externalJavaScript.js"> in <head>

- JavaScript will be loaded before the HTML page content gets loaded.
- Page load can get slower as before loading page, scripts need to be fetched and executed.

### <script src="externalJavaScript.js"> in <body>

- HTML page content will get loaded before executing script, so page load will be faster. 


## Event Handlers : EventTarget Interface

In JavaScript we have an interface *EventTarget* which is implemented by objects which
need to receive events and add listeners to those events.

Following objects do implement *EventTarget*

- Element and it's children
- Document
- Window
- IDBRequest
- AudioNode
- AudioContext

*EventTarget* provides the methods :
- addEventListener()
- removeEventListener()
- dispatchEvent()


### Event handling using addEventListener()

We know the objects in JavaScript which can fire events, do implement interface
*EventTarget* and thus have an *addEventListener()* method available to call.

Events can be added using addEventListener(), check below for example :
https://github.com/saurabh1088/JavaScript/blob/main/java-script-playground/external-in-separate-js-files/ExternalJavaScriptFile.js

Same object can make more than one call to addEventListener() and provide different
handlers and this is valid. This way one can have multiple handlers for a single
event. For e.g. below code is perectly valid.

```
someElement.addEventListener("click", functionEventHandlerOne);
someElement.addEventListener("click", functionEventHandlerTwo);
```

### Event handler properties

Objects which can fire events also have properties. For example, elements have a
property *onclick* to which one can assign a handler function and it will behave
in similar manner as using addEventListener().

For e.g. in below example calling and assigning again to onclick will override the
previous handler and thus only eventHandlerTwo will get called.

```
someElement.onclick = eventHandlerOne
someElement.onclick = eventHandlerTwo

function eventHandlerOne() {
  console.log("Event handler one");
}

function eventHandlerTwo() {
  console.log("Event handler two");
}
```

### Inline event handlers - NOT RECOMMENDED

In example mentioned at below HTML for button with id *changeBackgroundColorToRed*
one can also set event handler inline like below

https://github.com/saurabh1088/JavaScript/blob/main/java-script-playground/embedded-using-script-tag/html-with-embedded-javascript.html

One important point to note here is that in quotes for attribute onclick one needs
to use brackets (), otherwise it will not work.

```
<button id="changeBackgroundColorToRed" onclick="changeColorToRed()">Red</button>
```

This way was very early way of managing event handlers. There are many HTML attributes
like one in example above - *onclick*, however these are NOT RECOMMENDED to use.

This way is like mixing HTML and JavaScript, which should be separate. Keeping HTML
and JavaScript code separate and in separate files is a good practice and it helps
code re-use as well.


## Event Objects

Event handler functions can have parameter specified with some name which is event
object, this object gets automatically passed to event handler function to provide
extra information. For e.g.

Full example details in file :
https://github.com/saurabh1088/JavaScript/blob/main/java-script-playground/events-in-javascript/events.js

```
function eventHandlerExploringEventObject(event) {
  console.log("Here's the event object received...")
  console.log(event)
}
```

## Preventing Default Behaviour

For example, we have a scenario where there is a form in HTML with some input fields,
when submit action is performed form will get submitted. Form submission is the
default behaviour of submit action.

### What is the default behaviour of form submission?

HTML form tag has an *action* attribute. This attribute specifies where to send
the form-data when a form is submitted. So by default when submit action is performed
as per action attribute all form data will be send to it.

Now suppose before sending data right away to action attribute, we want to perform
some validation, then based on certain conditions we need to skip the default behaviour
of form submission. This is where *preventDefault()* comes into play.
*preventDefault()* method comes from *Event* interface.

Example link :
https://github.com/saurabh1088/JavaScript/tree/main/java-script-playground/events-in-javascript

## Event bubbling

Event Bubbling is a concept in DOM(Document Object Model) which happens when an element
receives an event and the event gets transmitted or propagated to its parent elements
till it gets to the root element. One can say the event bubbles up, hence the terminology.

This is the default behaviour of events on elements unless stopped explicitly.

### How to prevent unexpected event bubbling?

As event bubbling to parent elements is default behaviour, it can sometimes create
issue. So sometimes if required to prevent this default behaviour one can use
*stopPropagation()* method from Event interface. *stopPropagation()* when called
inside event handler will prevent the event from bubbling up to other elements.

Example link :
https://github.com/saurabh1088/JavaScript/tree/main/java-script-playground/events-in-javascript

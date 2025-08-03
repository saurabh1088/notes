#  JavaScript QnA

---

## Explain JavaScript in terms of value type and reference type semantics, what happend in it.
- JavaScript does not adhere to a single semantic model.
- JavaScript employs value types and reference types both.

### Value types
- Primitive data types are value types like
    - String
    - Number
    - Boolean
    - null
    - undefined
    - Symbol
    - BigInt

### Reference types
- Object
- Array
- Function
- Date
- RegExp etc

---

## What Is the JavaScript Runtime Environment?
- The JavaScript Runtime Environment (JRE) is not part of JavaScript itself—it’s the ecosystem in which JavaScript code executes.
- JavaScript by itself is just a language specification (ECMAScript)
- It doesn’t define how code interacts with the outside world—no network requests, no file system access, no timers.

### So what does the runtime provides?
- The runtime environment provides
    - The engine (e.g., V8, SpiderMonkey) that parses and executes JS.
    - APIs to interact with the system (DOM, HTTP, File System, Timers).
    - The event loop and task queues to handle asynchronous operations.

### Analogy
- One can think like
    - JavaScript is the language.
    - The runtime environment is the operating system for JavaScript.

### Key Components of a JavaScript Runtime
#### JavaScript Engine
- Core of the runtime; executes code.
- Includes
    - Call Stack – Executes functions in LIFO order.
    - Heap – Stores objects and data.
    - Garbage Collector – Frees unused memory.
- Examples
    - V8 (Chrome, Node.js)
    - SpiderMonkey (Firefox)
    - JavaScriptCore (Safari)

#### WeWeb APIs / Host APIs
- In browser
    - DOM
    - Fetch API
    - setTimeout
    - Geolocation
    - WebSockets, etc.
- In Node.js
    - File system (fs)
    - HTTP modules
    - process
    - streams, etc.

#### Event Loop and Task Queues
- These enable non-blocking I/O, making JavaScript efficient for I/O-heavy applications.
    - Event Loop
        - Coordinates execution of synchronous and asynchronous code.
    - Task Queues
        - Macro-tasks (e.g., setTimeout callbacks, I/O events)
        - Micro-tasks (e.g., Promises, Mutation Observers)

---
#  Node.js


## What is Node.js?

Node.js is an 
- asynchronous 
- event-driven 
- open-source
- cross-platform
JavaScript runtime environment allowing one to execute JavaScript code server-side.

Node.js is a runtime environment that lets one run JavaScript code outside of a browser — usually on the server.

Node is NOT a Programming Language
Node is NOT a Framework

Node IS a Runtime Environment for executing JavaScript code. 

Node.js is built on V8 JavaScript runtime engine.
V8 JavaScript engine is the core of Google Chrome.
Node.js enables the execution of JavaScript on the server, outside the context of a web browser.

Node.js is designed to build scalable network applications which can handle multiple connections concurrently. Each
connection will fire a callback and if no work is to be done then Node.js will sleep.

As a Node.js app runs as a single process, it doesn't creates a new thread for every request.

What Node.js has enabled is that one can write JavaScript for browser for front-end UI can now also write server-side
code without needing to learn new language.

Node.js whenever performs an I/O operation, instead of blocking thread and wasting CPU cycles it only resumes operation
once response comes back.


## A Node.js Hello World Server

Below code saved in a *.js* file for e.g. Server.js can be executed as below to 
run a server.

```
node Server.js
```

```
const http = require('http');
const hostname = '127.0.0.1';
const port = 3000;
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});
server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

## Browser vs Node.js Application

First of all a common aspect of a browser and a Node.js application is JavaScript. Both browser and Node.js provide
environment allowing JavaScript code to execute.

However building an application which runs in a browser is altogether different from a Node.js application.

We don't have window or document in Node, these are available as a part of runtime environment available with browsers.

*window* is a global object present in browsers.
*global* is a global object present in Node.

| Browser                                                              | Node.js |
|---|---|
| Client side environment                                              | Server side environment |
| JavaScript is executed within context of a web browser               | JavaScript is run on server |
| JavaScript here can perform DOM manipulation                         | NO DOM manipulation  |
| Browser being event driven, JavaScript here is used to handle events | Used to build server side applications |


## Asynchronous and Non-Blocking

Node.js is asynchronous and non-blocking. 
Node applications are asynchronous and non-blocking BY DEFAULT

This is the reason Node is IDEAL for building I/O-intensive apps.
Node SHOULD NOT be used for CPU-intensive apps.

Frameworks like ASP.NET or Rails are synchronous and blocking by default so the way they operate is when a request comes
then a thread is allocated to handle the request and that thread will then not take up any other task till the request is
served. Now if the request takes time to complete, the thread will be waiting and doing nothing.
So in this case if number of requests increases more threads will get created and at some point maximum thread will reach
and further requests will have to wait till a thread gets free. Now to serve more requests/clients one has to throw in
more hardware.

JavaScript is designed to be non-blocking on the *main* thread, somewhat similar to how in iOS applications it is expected
to have all UI operations on main thread.
If not for this behaviour then one will experience UI freezing.


## Node Module System

Variables by default get added to global scope, which can lead to conflict if same name is used in multiple places.
Hence a modularity is required to avoid this problem.

Every file in Node.js is considered a module. All functions and variables defined in the file are private and by default
not accessible outside of the file. In order to use outside one has to explicitly export these. One only need to export
the variables and functions that need to be accessed from outside of module, rest all which aren't required can stay
private or un-exported.

### Module wrapper function


## JSHint

## libuv

JavaScript is synchronous, blocking, single threaded programming language. Node.js we defined above as asynchronous and
non-blocking which is possible with the help of *libuv*

## Behind the scenes
We have a client which makes a http call. The call eventually will be processed at a server hosted in a machine on a port.
By default the port is 80. All requests by default come on port 80. The machine may have various services running on
different ports. Based on http request the request will be directed to relevant port. Node.js doesn't have the capability
to listen to incoming network traffic. This is where *libuv* comes into play. *libuv* is an interface between the computer
and the Node.js. Computer has the hardware to listen to incoming requests but someone needs to pass this to Node.js for
further processing, that's where *libuv* chips in.

An incoming request to the computer where server is hosted is not in textual format. It's in streams of data or bytes.
*libuv* has sections handling incoming requests and outgoing responses.

Requests are mostly consisted of properties. Whereas responses are majorily methods. For example one of the methods in
response is end(), as responses are also sent as streams so the end() will let receiver know where response has ended.

There are event emitters. JavaScript defines routes, where different routes will handle different functionality.
So *libuv* will look for route in the incoming request and emit an event and then Node.js will execute the function
associated with that route as per definition. While executing the route defined method, Node.js will also provide access
to request as well.


## Event Loop

Node handles requests using an Event loop inside the NodeJS environment. Event could be anything. Event loop basically
could be defined as an event listener which funtions inside Node.js and is always ready to listen, process and output
for some event.

Technically *Event Loop* is just a C program and it is a part of *libuv*.

Event loop is alive as long as the Node.js application is up and running.

There are six queues which are part of every event loop in every iteration.

All synchronous JavaScript code will take priority over async code.


### Question : When some async task completes in libuv then when does Node runs the
associated callback?

Ans: Normal flow of execution will not be interrupted, callback functions will be
executed only when call stack becomes empty.


## .js vs .mjs in Node.js: What’s the Difference?


## What is Chrome's V8 JavaScript Engine?
The V8 JavaScript engine is Google Chrome’s open-source JavaScript and WebAssembly engine. It’s the part of the browser
(and Node.js) that executes JavaScript code.


## What is V8?
- V8 is a high-performance JavaScript engine written in C++.
- It was developed by Google for use in Chrome, but it’s now used beyond the browser — like in Node.js to run JavaScript on servers.

### What does V8 do?

#### Parses and Compiles JavaScript
- When JavaScript is run the V8
  - Parses the code into an Abstract Syntax Tree (AST)
  - Converts the AST into bytecode
  - Optimizes that into machine code for CPU

Note : It’s like how LLVM compiles Swift into optimized native code.

#### Optimizes Performance
- V8 includes
  - JIT (Just-In-Time) Compiler: Translates JavaScript into native machine code at runtime.
  - Inline Caching, Hidden Classes, and other runtime optimizations.


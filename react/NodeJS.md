#  Node.js


Node.js is an 
- asynchronous 
- event-driven 
- open-source
- cross-platform
JavaScript runtime environment allowing one to execute JavaScript code server-side.

Node is NOT a Programming Language
Node is NOT a Framework

Node IS a Runtime Environment for executing JavaScript code. 

Node.js is built on V8 JavaScript runtime engine.
V8 JavaScript engine is the core of Google Chrome.
Node.js enables the execution of JavaScript on the server, outside the context 
of a web browser.

Node.js is designed to build scalable network applications which can handle multiple
connections concurrently. Each connection will fire a callback and if no work is 
to be done then Node.js will sleep.

As a Node.js app runs as a single process, it doesn't creates a new thread for 
every request.

What Node.js has enabled is that one can write JavaScript for browser for front-end
UI can now also write server-side code without needing to learn new language.

Node.js whenever performs an I/O operation, instead of blocking thread and wasting
CPU cycles it only resumes operation once response comes back.


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

First of all a common aspect of a browser and a Node.js application is JavaScript.
Both browser and Node.js provide environment allowing JavaScript code to execute.

However building an application which runs in a browser is altogether different
from a Node.js application.

We don't have window or document in Node, these are available as a part of runtime
environment available with browsers.

*window* is a global object present in browsers.
*global* is a global object present in Node.

| Browser                                                              | Node.js |
| Client side environment                                              | Server side environment |
| JavaScript is executed within context of a web browser               | JavaScript is run on server |
| JavaScript here can perform DOM manipulation                         | NO DOM manipulation  |
| Browser being event driven, JavaScript here is used to handle events | Used to build server side applications |


## Asynchronous and Non-Blocking

Node.js is asynchronous and non-blocking. 
Node applications are asynchronous and non-blocking BY DEFAULT

This is the reason Node is IDEAL for building I/O-intensive apps.
Node SHOULD NOT be used for CPU-intensive apps.

Frameworks like ASP.NET or Rails are synchronous and blocking by default so the
way they operate is when a request comes then a thread is allocated to handle the
request and that thread will then not take up any other task till the request is
served. Now if the request takes time to complete, the thread will be waiting and
doing nothing.
So in this case if number of requests increases more threads will get created and
at some point maximum thread will reach and further requests will have to wait till
a thread gets free. Now to serve more requests/clients one has to throw in more
hardware.


## Node Module System

Variables by default get added to global scope, which can lead to conflict if same
name is used in multiple places. Hence a modularity is required to avoid this problem.

Every file in Node.js is considered a module. All functions and variables defined
in the file are private and by default not accessible outside of the file. In order
to use outside one has to explicitly export these. 
One only need to export the variables and functions that need to be accessed from
outside of module, rest all which aren't required can stay private or un-exported.

### Module wrapper function


## JSHint

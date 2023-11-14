#  Node.js


Node.js is an 
- asynchronous 
- event-driven 
- open-source
- cross-platform
JavaScript runtime environment allowing one to execute JavaScript code server-side.

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

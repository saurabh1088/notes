#  JavaScript Just-In-Time (JIT) Compilation


## What Is JIT Compilation?
- Just-In-Time (JIT) compilation is a technique where code is compiled into native machine code during the execution of a program—not before the program runs.
- This approach combines aspects of both pure interpretation and ahead-of-time (AOT) compilation, delivering a balance between flexibility and performance.
- JIT is looking at the program running and optimising it afterwards it observed it running.


## The Problem with Traditional Interpretation
- In a purely interpreted language, a program's source code is read and executed line by line by an interpreter.
- This is flexible but slow.
- For a loop that runs 1,000 times, the interpreter would have to read, parse, and execute the same code 1,000 times.
- This is highly inefficient for "hot" code—code that is executed frequently.


## How JIT Compilation Works?
- JIT compilation aims to solve this inefficiency of traditional interpretation.
- Instead of just interpreting code, JIT compilers observe and analyze the code as it runs.
- The core idea is to identify the "hot" code and compile it into highly optimized machine code at runtime.
- This compiled code can then be executed much faster on subsequent runs.


## References
- https://www.youtube.com/watch?v=d7KHAVaX_Rs




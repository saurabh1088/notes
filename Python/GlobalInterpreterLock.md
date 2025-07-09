# Global Interpreter Lock


## What is Global Interpreter Lock?
- The Global Interpreter Lock (GIL) is a mutex (a type of lock) that protects access to Python objects, preventing multiple
native threads from executing Python bytecodes simultaneously.
- In simpler terms, it's a mechanism that ensures only one thread can execute Python code at any given time, even on
multi-core processors.
- This means that only one thread can be in a state of execution at any point in time in Python(CPython).
    - This doesn’t apply to I/O-bound tasks or non-CPython implementations (like Jython or IronPython) which don't have a GIL.


## What this means for developers?
- The impact of the GIL isn’t visible to developers who execute single-threaded programs. 
- But it can be a performance bottleneck in CPU-bound and multi-threaded code.

## Why is GIL gained reputation of an “infamous” feature of Python?
- GIL enforces that only one thread can execute Python bytecode at any given time, regardless of the number of threads or
CPU cores.
- This restriction is present even on multi-core systems where hardware would otherwise allow true parallel execution of
multiple threads.
- As a result of this
    - Multi-threading in Python is effective for I/O-bound tasks (e.g., network calls, file reads).
    - But it is ineffective for CPU-bound tasks, where the GIL prevents threads from executing in parallel.
    - It limits Python's ability to fully utilize multi-core processors in CPU-heavy applications.
    - It surprises many developers coming from other languages where threads can run truly in parallel.
- This all has led to the GIL being called an “infamous” feature of Python.

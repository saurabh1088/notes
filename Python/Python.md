# Python

## 1. What is CPython? Is it difference from Python?
- From official documentation https://docs.python.org/3/reference/introduction.html#alternate-implementations
    - CPython is the original and most-maintained implementation of Python, written in C.
    - New language features generally appear for CPython first.
- CPython is the original default Python implementation, written in C.
- It's called as CPython to distinguish it from the other Python implementations.
- Python is a language.
- CPython is the implementation of Python in C.

## 2. Objects
- Python being OOP language, objects form abstraction for data.
- Every object in Python has
    - Identity
        - *id()* function returns an integer representing identity of an object.
        - *is* operator compares identity of two objects.
    - Type
        - *type()* function returns an object's type.
    - Value
- Identity and Type of an Object in Python is unchangeable.
- Objects in Python are never explicitly destroyed, once they are unreachable, then they may be garbage collected.


## 3. Garbage collection
- Python primarily uses two mechanisms to implement garbage collection
    - Reference counting
    - Generational garbage collection
    these two work together to ensure memory is managed efficiently.
- Using gc module, one can enable or disable automatic garbage collection.

### 3.1 Reference counting
- Python uses a reference-counting scheme.
- Python tracks number of references to every object in memory.
- Reference count of an object increases or decreases based on if a new reference is made to object or existing one is deleted.
- Object is said to become unreachable when the reference count drops to 0.
- When object is unreachable, Python automatically deallocates the memory it occupies.

#### 3.1.1 Limitation in reference counting
- Most prominent limitation is inability to handle cyclic references.
- Cyclic references are when two objects are referencing to each other forming a cycle.
- Cyclic references causes objects involved in cyclic reference not getting unreachable, preventing memory from being reclaimed.
- This is where generational garbage collection comes in.

### 3.1.2 How to get reference count for an object?
The reference count can be examined using the sys.getrefcount() function. One important note about this function is that
the value returned by this function is always 1 more as the function also has a reference to the object when called.
Check example *example_reference_counting()* at below location:
https://github.com/saurabh1088/python/blob/main/learnings/concepts.py

### 3.2 Generational garbage collection
- Overcomes limitations of reference counting with respect to cyclic references.
- Python's garbage collector organizes objects into three generations
    - Generation 0 (youngest)
    - Generation 1 (middle-aged)
    - Generation 2 (oldest)
- New objects are placed in Generation 0, when those survive garbage collection, those are moved to next generation.
- Garbage collector runs more frequently on younger objects i.e. Generation 0.
- As objects move to higher generations, those are collected less frequently.
    - This approach is taken to focus on objects more likely to be discarded soon.
- During collection process, garbage collector detects cyclic references and reclaims the memory.


## References
- https://www.datacamp.com/tutorial/python-garbage-collection
- https://github.com/python/cpython/blob/main/InternalDocs/garbage_collector.md


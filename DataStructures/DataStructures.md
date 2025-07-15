# Data Structures

_Data structure is a way of organising data such that it can be used effectively_


## Real world analogy
- One can think of it like organizing one's physical belongings:
    - If one just throw all their clothes into a pile, it's hard to find a specific shirt (inefficient access).
    - If one fold them and put them in drawers by type (shirts in one, pants in another), it's much easier (organized for efficient access).
    - If one hang them in a closet by color, it's efficient for a different kind of access.


## Why Data Structures?
- These are essential ingredients to write fast, powerful algorithms solving problems.
- Manage and organise data efficiently
- Clean and organised code


## Abstract Data Type vs Concrete Implementations(Data Structures)

### Abstract Data Type (ADT)
- Abstract Data Type is a logical description or a mathematical model of a data type from the point of view of
    - how it behaves,
    - what operations can be performed on it, and 
    - what those operations do.
- It defines the what, not the how.
- It means the focus is on
    - behavior,
    - operations, and 
    - their conceptual properties (e.g., "add an element," "remove the last element," "check if empty")
- It doesn't specify how these operations are actually carried out or how the data is stored in memory.

#### Analogy
- Think of a "Stack" as an ADT.
- One knows one can push items onto it, pop items off the top, and peek at the top item. 
- One knows it's LIFO (Last-In, First-Out).
- One don't care how it's built inside, just that it behaves like a stack.

### Concrete Implementations
- A concrete implementation is the actual physical realization of an ADT in code.
- It defines the how.
- It specifies the underlying data structure (e.g., array, linked list) and the algorithms used to perform the ADT's operations.
- It focuses on
    - data storage details,
    - specific algorithms,
    - memory layout, and 
    - performance characteristics (Big O)

## The Big-O Notation
_Big-O notation is a mathematical concept which helps describing performance of an algorithm in terms of time and space relative to size of input_

1. Time Complexity
- Time complexity of an algorithm describes how runtime of the algorithm varies with the input size.
2. Space Complexity
- Space complexity of an algorithm describes how memory usage varies 


## Resources

https://www.youtube.com/playlist?list=PLDV1Zeh2NRsB6SWUrDFW2RmDotAfPbeHu


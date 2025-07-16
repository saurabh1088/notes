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

#### Analogy
- A Stack ADT can be concretely implemented using an Array (e.g., Python's list using append() and pop()).
- A Stack ADT can also be concretely implemented using a Linked List.
- Both implementations fulfill the "Stack" behavior, but they have different performance characteristics 
    - (e.g., array-based stack might be faster for pop if it doesn't need to reallocate,
    - but linked list based stack might be better if memory is highly fragmented).

| ADT (Abstract Data Type) | Common Concrete Implementations            | Key Behavior/Purpose                                 |
| :----------------------- | :----------------------------------------- | :--------------------------------------------------- |
| List                     | Array                                      | Ordered sequence, random access, mutable.            |
| Stack                    | Array, Linked List                         | LIFO (Last-In, First-Out) operations.                |
| Queue                    | Array, Linked List, Circular Buffer        | FIFO (First-In, First-Out) operations.               |
| Map / Dictionary         | Hash Table                                 | Key-value pairs, fast lookups.                       |
| Set                      | Hash Table, Balanced Binary Search Tree    | Collection of unique items, fast membership test.    |
| Graph                    | Adjacency List, Adjacency Matrix           | Represents relationships between entities.           |
| Tree                     | Node-based structures                      | Hierarchical data, efficient searching/sorting.      |


## The Big-O Notation
_Big-O notation is a mathematical concept which helps describing performance of an algorithm in terms of time and space relative to size of input_

- Big O notation describes the worst-case scenario for
    - how the runtime or space requirements of an algorithm grow with the input size.
- It's not about exact time in seconds, but about the rate of growth.

### Time Complexity
- Time complexity of an algorithm describes how runtime of the algorithm varies with the input size.

### Space Complexity
- Space complexity of an algorithm describes how memory usage varies


## O(1) - Constant Time

### Meaning
- The time it takes to complete the operation remains constant, regardless of the input size. 
- It doesn't matter if one have 1 item or a million items; the operation takes roughly the same amount of time.

### Analogy
- Finding a book on a shelf when one knows its exact position (e.g., "the 3rd book from the left")
    - It takes the same effort whether the shelf has 10 books or 1000 books.
    - One just go directly to that spot.

### Examples
- Accessing an element in an array by its index (my_list[5]).
- Adding an element to the end of a Python list (my_list.append(item) - amortized).
- Accessing a value in a hash table (dictionary) by its key (my_dict['key']).


## O(n) - Linear Time

### Meaning
- The time it takes to complete the operation grows linearly with the input size.
- If one doubles the input size, the time roughly doubles.

### Analogy
- Finding a specific book on a shelf when one doesn't knows its position.
- So one have to look at each book one by one until one finds it.
    - If there are 10 books, one might look at up to 10.
    - If there are 100 books, one might look at up to 100.
    - The effort scales directly with the number of books.

### Examples
- Searching for an item in an unsorted list (item in my_list).
- Iterating through all elements of an array or linked list (for item in my_list:).
- Copying an array.


## O(n^2) - Quadratic Time

### Meaning
- The time it takes to complete the operation grows proportionally to the square of the input size.
- If one doubles the input size, the time roughly quadruples.
- This is often seen with nested loops.

### Analogy
- Imagine a classroom with n students.
    - Teacher asks each student to shake hands with every other student exactly once.

### Examples
- Nested loops where each loop iterates over the entire input (e.g., simple sorting algorithms like Bubble Sort or Selection Sort).
- Comparing every element in a list to every other element.


## O(log n) - Logarithmic Time

### Meaning
- The time it takes to complete the operation decreases as the input size grows, but at a very slow rate.
- It's incredibly efficient. This often happens when the algorithm repeatedly halves the search space.

### Analogy
- Finding a word in a dictionary (a physical one).
    - One doesn't check every word.
    - One opens to the middle.
    - Is word before or after?
    - Then open to the middle of that half.
    - Keep halving the search space until one find it.


### Examples
- Binary search on a sorted array.
- Inserting or searching in a balanced binary search tree.


## Resources

https://www.youtube.com/playlist?list=PLDV1Zeh2NRsB6SWUrDFW2RmDotAfPbeHu


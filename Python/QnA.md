# Python QnA


## How do generators differ from iterators in Python?

In Python, both generators and iterators are fundamental concepts related to iteration, but they differ in their creation
and how they function.

Here's a breakdown of their differences:

### Iterators

An **iterator** is an object that represents a stream of data. It implements the iterator protocol, which consists of two methods:

- `__iter__(self)`:  
    Returns the iterator object itself. This allows an object to be iterable (meaning you can use it in a `for` loop).

- `__next__(self)`:  
    Returns the next item from the sequence. If there are no more items, it must raise the `StopIteration` exception.

**Key characteristics of iterators:**

- **Explicitly Defined:**  
    You typically define an iterator by creating a class that implements the `__iter__` and `__next__` methods.

- **Stateful:**  
    Iterators maintain their internal state (i.e., where they are in the sequence) to know what the next item is.

- **Manual Implementation:**  
    Creating custom iterators often involves more boilerplate code.

- **Can be Finite or Infinite:**  
    Iterators can represent a finite sequence (like a list) or an infinite sequence (like counting numbers).


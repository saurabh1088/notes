# Data Structures PnA


-----

## 30-Day Data Structures Learning Plan (Python Focus)

**Assumed Prior Knowledge:** Basic programming concepts (variables, data types, `if/else`, `for`/`while` loops, functions, basic OOP concepts like classes and objects).
**Daily Commitment:** 30 minutes (15 min Theory + 15 min Hands-on Coding)
**Programming Language:** Python (with notes on its suitability)
**Goal:** Confidently understand, implement, and choose appropriate data structures.

-----

### Phase 1: Foundations & Linear Structures (Days 1-7)

**Day 1: Introduction to Data Structures & Big O Notation**

  * **Theory (15 min):** What are Data Structures (DS)? Why do we need them? Introduction to Abstract Data Types (ADTs) vs. concrete implementations. **Big O Notation:** Explain O(1), O(n), O(n^2), O(log n), O(n log n) with simple analogies (e.g., finding a book on a shelf vs. in a library). Emphasize measuring *how performance scales* with input size.
  * **Hands-on (15 min):**
      * Write simple Python functions: one with O(1) operation (e.g., list access by index), one with O(n) (e.g., linear search), one with O(n^2) (e.g., nested loop).
      * Time their execution for small and large inputs (`time` module).
  * **Practice Task:** Write a Python function that takes a list and returns `True` if it contains duplicates, `False` otherwise. Analyze its Big O complexity.
  * **References:**
      * [Big O Notation Explained](https://www.freecodecamp.org/news/big-o-notation-explained-with-examples/)
      * [Real Python: Big O Notation](https://www.google.com/search?q=https://realpython.com/lessons/big-o-notation/)

**Day 2: Arrays (Lists in Python)**

  * **Theory (15 min):** Concept of an array (contiguous memory). Python's `list` as a dynamic array.
      * Operations: Accessing elements by index (O(1)), Appending (amortized O(1)), Inserting/Deleting at arbitrary position (O(n)), Searching (O(n)).
      * Trade-offs: Fast reads, slow middle modifications.
  * **Hands-on (15 min):**
      * Create lists, access elements, slice.
      * Use `append()`, `insert()`, `pop()`, `del` to modify lists.
      * Time `append()` vs. `insert(0, ...)` for large lists to observe O(n) overhead.
  * **Practice Task:** Implement a function `reverse_list(my_list)` that reverses a list in-place without using `my_list.reverse()`. Analyze its complexity.

**Day 3: Linked Lists - Singly Linked List (Conceptual & Basic Implementation)**

  * **Theory (15 min):** Introduction to Linked Lists (nodes, head, pointer/reference). Contrast with arrays (non-contiguous memory).
      * Operations: Traversal (O(n)), Insertion at head (O(1)), Insertion at tail (O(n) without tail pointer, O(1) with), Deletion at head (O(1)), Deletion of specific node (O(n)).
      * Trade-offs: Flexible insertions/deletions, slow random access.
  * **Hands-on (15 min):**
      * Define a `Node` class.
      * Define a `SinglyLinkedList` class with `head` attribute.
      * Implement `append_at_head(data)` and `display()` methods.
  * **Practice Task:** Add a `search(data)` method to your `SinglyLinkedList` that returns `True` if data is found, `False` otherwise.

**Day 4: Stacks (LIFO)**

  * **Theory (15 min):** Abstract Data Type: Stack (Last-In, First-Out).
      * Core Operations: `push` (add element), `pop` (remove top element), `peek` (view top element), `is_empty`.
      * Implementation: Using Python's `list` (`append()` for push, `pop()` for pop). Analyze Big O for each.
      * Real-world uses: Function call stack, undo/redo, browser history.
  * **Hands-on (15 min):**
      * Implement a `Stack` class using a Python list.
      * Perform `push`, `pop`, `peek`, `is_empty` operations.
      * Observe LIFO behavior.
  * **Practice Task:** Write a function `check_parentheses(expression)` that uses a stack to determine if parentheses in a string are balanced (e.g., "({[]})" is balanced, "([)]" is not).

**Day 5: Queues (FIFO)**

  * **Theory (15 min):** Abstract Data Type: Queue (First-In, First-Out).
      * Core Operations: `enqueue` (add element), `dequeue` (remove front element), `peek` (view front element), `is_empty`.
      * Implementation: Using Python's `list` (`append()` for enqueue, `pop(0)` for dequeue - **note O(n) for pop(0)**). Introduce `collections.deque` for efficient queue operations (O(1) for both ends).
      * Real-world uses: Task scheduling, print queues, BFS graph traversal.
  * **Hands-on (15 min):**
      * Implement a `Queue` class using `collections.deque`.
      * Perform `enqueue`, `dequeue`, `peek`, `is_empty` operations.
      * Observe FIFO behavior.
  * **Practice Task:** Simulate a customer service line where customers arrive and are served in order.

**Day 6: Hash Tables (Dictionaries in Python)**

  * **Theory (15 min):** Concept of hashing, key-value pairs. How hash functions map keys to indices. Collision resolution (briefly: chaining, open addressing).
      * Python's `dict` as a highly optimized hash table.
      * Operations: Insertion, Deletion, Lookup (average O(1), worst-case O(n) due to collisions).
      * Trade-offs: Fast average-case performance, unordered (pre-3.7), memory overhead.
  * **Hands-on (15 min):**
      * Create dictionaries, add/remove/access items.
      * Experiment with different key types (strings, numbers, tuples).
      * Time dictionary lookups for large dictionaries vs. list searches.
  * **Practice Task:** Write a function `word_frequency(text)` that takes a string and returns a dictionary where keys are words and values are their frequencies.

**Day 7: Doubly Linked Lists (Briefly) & Circular Linked Lists (Conceptual)**

  * **Theory (15 min):** Doubly Linked List (nodes with `prev` and `next` pointers). Advantages (bidirectional traversal, O(1) deletion if node reference available). Disadvantages (more memory, complex implementation). Circular Linked List (tail points to head).
  * **Hands-on (15 min):**
      * Modify your `Node` class to include a `prev` pointer.
      * Implement `append_at_tail()` for a `DoublyLinkedList`.
  * **Practice Task:** Implement a method `delete_node(node)` in your `DoublyLinkedList` that deletes a given node in O(1) time (assuming you have the node reference).

-----

### Phase 2: Non-Linear Structures & Advanced Concepts (Days 8-15)

**Day 8: Trees - General Tree Concepts & Binary Trees**

  * **Theory (15 min):** Introduction to Trees (Root, Node, Child, Parent, Leaf, Edge, Path, Depth, Height). Binary Trees (max 2 children per node).
      * Real-world uses: File systems, organizational charts, XML/HTML DOM.
  * **Hands-on (15 min):**
      * Define a `TreeNode` class with `data`, `left`, `right`.
      * Construct a simple binary tree manually (e.g., a small tree for an expression).
  * **Practice Task:** Implement a function `get_height(node)` that calculates the height of a binary tree.

**Day 9: Tree Traversal - BFS & DFS**

  * **Theory (15 min):**
      * **Depth-First Search (DFS):** Pre-order, In-order, Post-order traversal. Explain recursive implementation.
      * **Breadth-First Search (BFS):** Level-order traversal. Explain using a queue.
      * Analyze Big O for traversal (O(N) where N is number of nodes).
  * **Hands-on (15 min):**
      * Implement recursive DFS traversals (in-order, pre-order, post-order) for your `TreeNode`.
      * Implement BFS traversal for your `TreeNode` using `collections.deque`.
  * **Practice Task:** Print the elements of your tree in pre-order traversal.

**Day 10: Binary Search Trees (BSTs)**

  * **Theory (15 min):** Properties of a BST (left child \< parent \< right child).
      * Operations: Insertion (average O(log n), worst O(n)), Search (average O(log n), worst O(n)).
      * Trade-offs: Efficient search for ordered data, but can become unbalanced.
  * **Hands-on (15 min):**
      * Implement `insert(data)` method for your `BSTNode`.
      * Implement `search(data)` method.
  * **Practice Task:** Implement a function `find_min(node)` and `find_max(node)` in your BST.

**Day 11: Heaps - Min-Heap & Max-Heap**

  * **Theory (15 min):** Heap property (parent value vs. children values). Binary Heap (complete binary tree, usually array-based implementation).
      * Operations: `insert` (O(log n)), `extract_min/max` (O(log n)), `heapify` (O(n)).
      * Real-world uses: Priority Queues, Heap Sort.
  * **Hands-on (15 min):**
      * Implement a basic Min-Heap using a Python list (focus on `insert` and `_heapify_up`).
      * Use Python's `heapq` module for quick heap operations.
  * **Practice Task:** Use `heapq` to find the K smallest elements in a list.

**Day 12: Graphs - Representation**

  * **Theory (15 min):** Vertices (nodes), Edges. Directed vs. Undirected. Weighted vs. Unweighted.
      * Representations: **Adjacency List** (list of lists or dictionary of lists - preferred for sparse graphs), **Adjacency Matrix** (2D array - preferred for dense graphs).
      * Big O for representation and basic operations.
  * **Hands-on (15 min):**
      * Represent a simple undirected graph using an adjacency list (dictionary where keys are vertices, values are lists of neighbors).
      * Add methods to add vertices and edges.
  * **Practice Task:** Represent a small social network graph (people as vertices, friendships as edges).

**Day 13: Graph Traversal - BFS**

  * **Theory (15 min):** Breadth-First Search (BFS). Explain its use for shortest path in unweighted graphs, finding all reachable nodes.
      * Algorithm: Use a queue, `visited` set.
      * Big O: O(V + E) where V is vertices, E is edges.
  * **Hands-on (15 min):**
      * Implement BFS for your graph representation.
      * Print nodes in BFS order.
  * **Practice Task:** Find if a path exists between two given nodes in your graph using BFS.

**Day 14: Graph Traversal - DFS**

  * **Theory (15 min):** Depth-First Search (DFS). Explain its use for connectivity, topological sorting, cycle detection.
      * Algorithm: Use recursion (or explicit stack), `visited` set.
      * Big O: O(V + E).
  * **Hands-on (15 min):**
      * Implement DFS for your graph representation.
      * Print nodes in DFS order.
  * **Practice Task:** Count the number of connected components in an undirected graph using DFS.

**Day 15: Introduction to Algorithms & DS Choice**

  * **Theory (15 min):** Brief intro to common algorithms (Sorting, Searching). How DS enable algorithms.
      * **Choosing the Right DS:** Discuss trade-offs (space vs. time), common use cases (e.g., hash table for fast lookups, array for indexed access, linked list for frequent insertions/deletions at ends).
  * **Hands-on (15 min):**
      * Given a few simple problem statements, discuss which DS would be most suitable and why.
      * Implement a simple sorting algorithm (e.g., Bubble Sort or Selection Sort) for a list. Analyze its complexity.
  * **Practice Task:** Given a stream of numbers, design a system (using appropriate DS) to efficiently find the median at any point.

-----

### Phase 3: Advanced Topics & Practical Application (Days 16-30)

**Day 16: Trees - Self-Balancing BSTs (Conceptual)**

  * **Theory (15 min):** Problem with unbalanced BSTs (O(n) worst case). Introduce AVL Trees, Red-Black Trees (conceptual, no implementation). Mention Python libraries that use them.
  * **Hands-on (15 min):**
      * Review BST insertion.
      * Discuss how rotations would conceptually fix imbalance.
      * Look up `sortedcontainers` library (uses balanced trees).
  * **Practice Task:** Research and summarize the key properties of a Red-Black Tree.

**Day 17: Tries (Prefix Trees)**

  * **Theory (15 min):** Concept of a Trie. Nodes representing characters.
      * Operations: Insertion, Search, Prefix Search (O(L) where L is length of word/prefix).
      * Real-world uses: Autocomplete, spell checkers, IP routing.
  * **Hands-on (15 min):**
      * Define a `TrieNode` class.
      * Implement `insert(word)` and `search(word)` in a `Trie` class.
  * **Practice Task:** Implement `starts_with(prefix)` method in your Trie.

**Day 18: Disjoint Set Union (Union-Find)**

  * **Theory (15 min):** Concept of Disjoint Sets. Operations: `union` (merge sets), `find` (find representative of a set). Path compression and Union by Rank/Size for optimization.
      * Real-world uses: Kruskal's algorithm (MST), connected components in a graph.
  * **Hands-on (15 min):**
      * Implement `find` with path compression.
      * Implement `union` by rank/size.
  * **Practice Task:** Use Union-Find to solve a simple connectivity problem (e.g., given a list of pairs representing friendships, determine if two people are in the same friend group).

**Day 19: Advanced Hashing & Collision Resolution**

  * **Theory (15 min):** Deeper dive into hash functions. Different collision resolution strategies (linear probing, quadratic probing, double hashing). Load factor.
  * **Hands-on (15 min):**
      * Implement a simple custom hash table with linear probing.
      * Observe how load factor affects performance.
  * **Practice Task:** Compare the performance of Python's `dict` vs. your custom hash table for large number of insertions and lookups.

**Day 20: String Algorithms & DS (Conceptual)**

  * **Theory (15 min):** Brief overview of string matching algorithms (KMP, Rabin-Karp - conceptual). Suffix Trees/Arrays (conceptual).
  * **Hands-on (15 min):**
      * Implement a naive string search algorithm.
      * Discuss how specialized DS can optimize this.
  * **Practice Task:** Find all occurrences of a pattern in a text (naive approach).

**Day 21: Introduction to Dynamic Programming (DP)**

  * **Theory (15 min):** Concept of DP (overlapping subproblems, optimal substructure). Memoization vs. Tabulation.
      * Real-world uses: Optimization problems, shortest path.
  * **Hands-on (15 min):**
      * Implement Fibonacci sequence using memoization.
      * Implement Fibonacci using tabulation.
  * **Practice Task:** Solve the "Climbing Stairs" problem using DP.

**Day 22: Greedy Algorithms**

  * **Theory (15 min):** Concept of Greedy algorithms (making locally optimal choices). When they work vs. when they don't.
      * Real-world uses: Coin change (sometimes), Dijkstra's algorithm.
  * **Hands-on (15 min):**
      * Implement a greedy coin change algorithm.
      * Discuss its limitations.
  * **Practice Task:** Solve the "Activity Selection Problem" using a greedy approach.

**Day 23: Backtracking & Recursion Revisited**

  * **Theory (15 min):** Deeper dive into recursion. Backtracking (exploring all options, then undoing).
      * Real-world uses: Sudoku solver, N-Queens problem, maze solving.
  * **Hands-on (15 min):**
      * Implement a recursive factorial function.
      * Implement a basic maze solver using backtracking.
  * **Practice Task:** Solve the N-Queens problem for a small N (e.g., N=4).

**Day 24: Bit Manipulation & DS (Conceptual)**

  * **Theory (15 min):** Basic bitwise operators (`&`, `|`, `^`, `~`, `<<`, `>>`). Bitmasks.
      * DS applications: Bitsets, Bloom Filters (conceptual).
  * **Hands-on (15 min):**
      * Perform basic bitwise operations.
      * Use bitmasks to represent sets of flags.
  * **Practice Task:** Check if a number is a power of 2 using bitwise operations.

**Day 25: Concurrency & Data Structures (Python Specific)**

  * **Theory (15 min):** Review GIL's impact on multithreading.
      * **Thread-safe collections:** `queue.Queue`, `collections.deque` (for atomic appends/pops from both ends).
      * `threading.Lock` for protecting custom shared mutable DS.
      * `multiprocessing` for true parallelism with DS (each process has its own DS copy, or use `multiprocessing.Queue`).
  * **Hands-on (15 min):**
      * Create a producer-consumer scenario using `queue.Queue` with multiple threads.
      * Demonstrate protecting a shared list with `threading.Lock`.
  * **Practice Task:** Implement a simple web crawler where multiple threads fetch URLs and add them to a shared, thread-safe queue for processing.

**Day 26: External Libraries for DS & Algorithms**

  * **Theory (15 min):** Introduce `collections` module (e.g., `Counter`, `defaultdict`, `namedtuple`).
      * `heapq` (built-in heap functions).
      * `networkx` (for graph algorithms).
      * `numpy` (for high-performance array operations).
  * **Hands-on (15 min):**
      * Use `collections.Counter` to count frequencies.
      * Use `collections.defaultdict`.
      * Experiment with `heapq` for priority queue.
  * **Practice Task:** Use `networkx` to find the shortest path in a small graph.

**Day 27: System Design & DS Choice**

  * **Theory (15 min):** How DS choices impact system performance, scalability, and memory footprint in larger applications.
      * Examples: Caching (hash tables), routing (graphs), search indexing (tries, hash tables), database indexing (trees).
      * Discuss trade-offs in real-world scenarios.
  * **Hands-on (15 min):**
      * Given a simplified system design problem (e.g., "design a URL shortener"), brainstorm appropriate data structures for different components.
  * **Practice Task:** Outline the data structures you would use for a simple in-memory key-value store and justify your choices.

**Day 28: Problem Solving Strategies with DS**

  * **Theory (15 min):** Common problem patterns and the DS/algorithms that solve them:
      * Finding unique elements (Set).
      * Maintaining order (List, Linked List, BST).
      * Fast lookups (Hash Table).
      * Priority management (Heap).
      * Connectivity (Graph, DSU).
  * **Hands-on (15 min):**
      * Solve a medium-difficulty problem from a platform like LeetCode, focusing on identifying the optimal data structure.
  * **Practice Task:** Solve the "Two Sum" problem using a hash table.

**Day 29: Review & Reinforcement**

  * **Theory (15 min):** Go through all your notes. Re-read Big O complexities. Draw out DS diagrams.
  * **Hands-on (15 min):**
      * Re-implement a few core DS (e.g., Stack, Queue, Hash Table) from scratch without looking at your previous code.
      * Solve a new mixed-concept problem.
  * **Practice Task:** Design and implement a simple LRU (Least Recently Used) Cache using a combination of a dictionary and a doubly linked list.

**Day 30: Capstone Project & Next Steps**

  * **Theory (15 min):** Reflect on your learning journey. Discuss areas for continued growth (e.g., advanced graph algorithms, specific tree types, algorithm design paradigms).
  * **Hands-on (15 min):**
      * **Capstone Project:** Start building a small, more complex application that leverages multiple data structures.
          * **Idea:** A simple **Route Finder** for a small map:
              * Represent the map as a **Graph** (adjacency list).
              * Implement **BFS** for shortest path (unweighted).
              * (Optional: If you learned enough, implement Dijkstra's using a **Min-Heap** for weighted shortest path).
              * Use **Dictionaries** for node lookups.
      * Plan out the project structure and begin coding the core DS components.
  * **References:**
      * [LeetCode](https://leetcode.com/): Excellent for practice problems.
      * [HackerRank](https://www.hackerrank.com/): Another great platform.
      * [GeeksforGeeks Data Structures](https://www.geeksforgeeks.org/data-structures/): Comprehensive tutorials.
      * [Algorithms Illuminated (Book Series)](https://www.algorithmsilluminated.org/): Good for deeper dives into algorithms.

-----

**General Tips for Success:**

  * **Consistency is Crucial:** Stick to the 30 minutes daily. Even if you don't finish a concept, the consistent exposure helps.
  * **Draw Diagrams:** For non-linear data structures (trees, graphs, linked lists), drawing them out on paper is incredibly helpful for understanding operations.
  * **Talk it Out:** Explain concepts to yourself or a rubber duck. If you can explain it simply, you understand it.
  * **Don't Just Copy:** Type out the code yourself. Debugging your own typos helps cement understanding.
  * **Python's Strengths:** Leverage Python's readability. Don't try to implement everything from scratch initially if Python has a highly optimized built-in (e.g., `dict` for hash tables). Understand the *concept* first, then how Python implements it, and then maybe try a basic custom implementation for learning.
  * **Error Handling:** Don't skip `try-except` blocks in your practice code.
  * **Testing:** As you progress, consider writing simple unit tests for your DS implementations.

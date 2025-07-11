# Python PnA

```
As an experienced developer with --UPDATE-ME-- years of --UPDATE-ME-- expertise, I want to learn Python by dedicating --UPDATE-ME-- minutes each day. Please create a structured, day-by-day learning plan starting from **today (--UPDATE-ME--)** that:

1. Builds progressively from Python basics to intermediate topics.
2. Combines **15 minutes of focused theory** with **15 minutes of hands-on coding** each day.
3. Includes:

   * **Core Python syntax and language fundamentals.**
   * **Object-Oriented Programming (OOP) in Python.**
   * **Error handling, file operations, and modules.**
   * **Iterators, decorators, and context managers.**
   * **Introductory concurrency and testing concepts.**
4. Suggests **mini-practice projects or exercises** for each topic.
5. Takes into account my existing programming knowledge to avoid unnecessary beginner-level explanations.

The goal is to achieve **practical fluency in Python within 30 days**, focusing on writing maintainable, production-quality code.
```

This is an ambitious yet achievable goal for a developer with your extensive Swift/Objective-C background! Your existing knowledge of programming paradigms, data structures, and software architecture will be a huge accelerator. This 30-day plan focuses on Python's unique aspects and common practices, blending theory with immediate hands-on application.

Here's your structured, day-by-day Python learning plan:

---

## 30-Day Python Fluency Plan for Experienced Swift/Obj-C Developers

**Goal:** Practical fluency in Python for production-quality code.
**Daily Commitment:** 30 minutes (15 min Theory, 15 min Hands-on Coding)
**Start Date:** Friday, July 11, 2025

---

### Phase 1: Core Python Fundamentals & Syntax (Days 1-7)

**Day 1: Python Environment & Basic Syntax**
* **Theory (15 min):** Python installation (Anaconda/Miniconda recommended for easy package management), `pip`. Jupyter Notebooks or VS Code for development. Python's philosophy (Zen of Python). Basic data types: `int`, `float`, `bool`, `str`. Variables (dynamic typing vs. Swift's static). `print()` function. Comments (`#`).
* **Hands-on (15 min):**
    * Install Python.
    * Open a Python interpreter or Jupyter Notebook.
    * Write `print("Hello, Python!")`.
    * Declare variables of different types and print their `type()`.
    * Experiment with basic string operations (concatenation, multiplication).
* **Mini-Project:** Create a script `hello_user.py` that asks for the user's name (`input()`) and prints a personalized greeting.

**Day 2: Operators & F-Strings**
* **Theory (15 min):** Arithmetic (`+`, `-`, `*`, `/`, `//`, `%`, `**`), comparison (`==`, `!=`, `>`, `<`, `>=`, `<=`), logical (`and`, `or`, `not`). Operator precedence. F-strings (Python's string interpolation, similar to Swift).
* **Hands-on (15 min):**
    * Write expressions using various operators.
    * Use f-strings to format output with variables and expressions.
    * Create a simple calculator that takes two numbers and an operator as input, then prints the result.
* **Mini-Project:** A small program that calculates the area of a rectangle given user input for length and width, printing the result using an f-string.

**Day 3: Control Flow**
* **Theory (15 min):** `if`, `elif`, `else` (indentation is key!). `for` loops with `range()`. `while` loops. `break` and `continue`. (Contrast with Swift's `if`/`for` syntax, no curly braces).
* **Hands-on (15 min):**
    * Write `if/elif/else` statements for different conditions.
    * Loop 10 times using `for` and `range()`.
    * Implement a `while` loop with a `break` condition.
* **Mini-Project:** A "Guess the Number" game: Python picks a random number (use `import random`), and the user gets a few tries to guess it, with hints.

**Day 4: Collections - Lists & Tuples**
* **Theory (15 min):** `list` (mutable, ordered, like Swift Arrays but more flexible types). Common list methods (`append`, `insert`, `remove`, `pop`, `sort`, `len`). Slicing. `tuple` (immutable, ordered, like Swift Tuples). When to use each.
* **Hands-on (15 min):**
    * Create lists and tuples.
    * Perform various list operations (add, remove, sort, slice).
    * Try to modify a tuple (observe error).
* **Mini-Project:** A simple "To-Do List" manager: allow adding tasks to a list, marking them complete (removing), and displaying all tasks.

**Day 5: Collections - Dictionaries & Sets**
* **Theory (15 min):** `dict` (mutable, unordered/insertion-ordered from Python 3.7+, key-value pairs, like Swift Dictionaries). Common dict methods (`keys`, `values`, `items`, `get`, `pop`). `set` (mutable, unordered, unique elements, like Swift Sets). Common set operations (union, intersection).
* **Hands-on (15 min):**
    * Create dictionaries and sets.
    * Add, access, modify, and remove elements from a dictionary.
    * Perform set operations.
* **Mini-Project:** Implement a simple contact book using a dictionary (name: phone number). Allow adding, looking up, and deleting contacts.

**Day 6: Functions - Definition & Arguments**
* **Theory (15 min):** `def` keyword. Positional arguments, keyword arguments. Default argument values. Arbitrary arguments (`*args` for positional, `**kwargs` for keyword). Return values. (Compare to Swift functions, highlight `*args`/`**kwargs` as unique).
* **Hands-on (15 min):**
    * Define functions with different types of arguments.
    * Call functions using positional and keyword arguments.
    * Experiment with `*args` and `**kwargs` to pass flexible arguments.
* **Mini-Project:** Create a function `calculate_average(*numbers)` that takes any number of numerical arguments and returns their average.

**Day 7: Comprehensions & Basic Generators**
* **Theory (15 min):** List comprehensions (`[expr for item in iterable if condition]`). Dictionary comprehensions. Set comprehensions. Generator expressions (lazy evaluation, `()`). (Relate to Swift's `map`, `filter`, `compactMap` operations on collections).
* **Hands-on (15 min):**
    * Rewrite loops using list, dict, and set comprehensions.
    * Create a simple generator expression and iterate over it.
* **Mini-Project:** Generate a list of squares for even numbers from 1 to 20 using a list comprehension. Create a generator for Fibonacci numbers.

---

### Phase 2: Object-Oriented Programming (OOP) in Python (Days 8-12)

**Day 8: Classes & Objects**
* **Theory (15 min):** `class` keyword. `__init__` (constructor), `self` (instance reference). Instance variables vs. class variables. Creating objects. (Compare to Swift classes, properties, initializers).
* **Hands-on (15 min):**
    * Define a simple `Person` class with `name` and `age` instance variables.
    * Add a `greet()` instance method.
    * Create multiple `Person` objects and call their methods.
* **Mini-Project:** Model a `Bank Account` class with `account_number`, `balance`, `deposit()`, and `withdraw()` methods.

**Day 9: Inheritance**
* **Theory (15 min):** Single inheritance (`class Child(Parent):`). `super().__init__()` for calling parent's constructor. Method overriding. (Compare to Swift inheritance).
* **Hands-on (15 min):**
    * Create `SavingsAccount` and `CheckingAccount` subclasses from `BankAccount`.
    * Override `withdraw()` in `SavingsAccount` to add a minimum balance check.
* **Mini-Project:** Extend your `Animal` class (from a previous example if you did one) into `Dog` and `Cat` subclasses, adding specific behaviors.

**Day 10: Polymorphism & Method Overriding**
* **Theory (15 min):** Deeper dive into polymorphism in Python (duck typing). How method overriding works. Importance of consistent method signatures.
* **Hands-on (15 min):**
    * Create a list of mixed `Animal`, `Dog`, `Cat` objects.
    * Call a common method (e.g., `make_sound()`) on each object in the list, observing polymorphic behavior.
* **Mini-Project:** Design a `Shape` base class with `area()` and `perimeter()` methods. Create `Circle` and `Rectangle` subclasses that override these methods.

**Day 11: Class Methods & Static Methods**
* **Theory (15 min):** `@classmethod` (takes `cls`), `@staticmethod` (takes no special args). Class variables (static properties). When to use each (revisit previous explanation with more depth).
* **Hands-on (15 min):**
    * Add a class variable `population_count` to your `Animal` class.
    * Add a `@classmethod` `create_animal_from_string(cls, data_string)` to `Animal` (factory method).
    * Add a `@staticmethod` `is_valid_name(name)` to `Animal`.
* **Mini-Project:** Refactor your `Bank Account` class to have a class method `create_new_account(initial_deposit)` and a static method `is_valid_account_number(account_num)`.

**Day 12: Encapsulation & Properties**
* **Theory (15 min):** Python's "private" (by convention, leading underscore `_name`) vs. "name mangling" (`__name`). Getters and Setters. `@property` decorator for creating "computed properties" (like Swift's computed properties).
* **Hands-on (15 min):**
    * Add a private-like attribute `_secret_data` to a class.
    * Implement a `@property` for `age` in your `Person` class to ensure it's always positive.
* **Mini-Project:** Enhance your `Bank Account` with a `@property` for `balance` that prevents direct modification and ensures `deposit`/`withdraw` are used.

---

### Phase 3: Error Handling, File Ops, Modules (Days 13-17)

**Day 13: Error Handling - `try/except`**
* **Theory (15 min):** `try`, `except` (specific exceptions), `else`, `finally`. Common built-in exceptions (`ValueError`, `TypeError`, `FileNotFoundError`). (Compare to Swift's `do/try/catch`).
* **Hands-on (15 min):**
    * Write code that might raise `ValueError` or `ZeroDivisionError` and catch them.
    * Use `else` and `finally` blocks.
* **Mini-Project:** Modify your `Calculator` to gracefully handle `ZeroDivisionError` and `ValueError` (e.g., if non-numbers are passed).

**Day 14: Custom Exceptions & Raising**
* **Theory (15 min):** Defining custom exception classes (inherit from `Exception`). Raising exceptions (`raise`).
* **Hands-on (15 min):**
    * Define a custom exception for your `Bank Account` class (e.g., `InsufficientFundsError`).
    * Modify `withdraw()` to `raise` this custom exception.
* **Mini-Project:** Create a function that validates user input (e.g., password strength) and raises a custom `InvalidInputError` if criteria are not met.

**Day 15: File I/O - Text Files**
* **Theory (15 min):** Opening files (`open()`), reading (`read()`, `readline()`, `readlines()`), writing (`write()`, `writelines()`). The `with open(...)` statement (context manager for auto-closing).
* **Hands-on (15 min):**
    * Create a text file and write lines to it.
    * Read the contents of a text file line by line.
    * Use `with open(...)` for safe file handling.
* **Mini-Project:** Write a script that reads a list of names from `names.txt` and writes them to `greeted_names.txt` with a "Hello, " prefix.

**Day 16: File I/O - Binary Files & OS Module**
* **Theory (15 min):** Basic binary file reading/writing (e.g., images, using `wb`/`rb` modes). Introduction to `os` module (path manipulation, directory listing, file existence checks) and `shutil` (copy, move, delete files/dirs).
* **Hands-on (15 min):**
    * Copy a small image file using `shutil.copy()`.
    * List files in a directory using `os.listdir()`.
    * Check if a file exists using `os.path.exists()`.
* **Mini-Project:** Create a simple file organizer that moves `.txt` files to a `TextFiles` folder and `.jpg` files to an `ImageFiles` folder within a specified directory.

**Day 17: Modules & Packages**
* **Theory (15 min):** `import` statement (`import module`, `from module import func`, `import module as alias`). `__init__.py` for packages. `sys.path`. How Python finds modules. (Compare to Swift's module system).
* **Hands-on (15 min):**
    * Create a simple module (`my_utils.py`) with a function.
    * Import and use it in another script.
    * Create a package with `__init__.py` and multiple modules.
* **Mini-Project:** Organize your "To-Do List" application into a package with separate modules for `Task` class, `TaskManager` logic, and `CLI` interface.

---

### Phase 4: Advanced Topics (Days 18-22)

**Day 18: Iterators & Iterables**
* **Theory (15 min):** What are iterables (`__iter__`) and iterators (`__next__`). How `for` loops work under the hood. Creating custom iterators. Generators (`yield` keyword) as a simpler way to create iterators.
* **Hands-on (15 min):**
    * Create a custom iterable class (e.g., `MyRange` that works like `range`).
    * Write a simple generator function (e.g., `countdown(n)`).
* **Mini-Project:** Implement a custom iterator for a `Playlist` class that iterates through songs.

**Day 19: Decorators - Basic**
* **Theory (15 min):** What decorators are (`@decorator_name`). How they work (functions that take a function and return a new function). Common use cases (logging, timing, authentication).
* **Hands-on (15 min):**
    * Create a simple decorator `time_it` that measures the execution time of a function.
    * Apply it to a dummy function.
* **Mini-Project:** Write a decorator `log_calls` that logs when a function starts and ends.

**Day 20: Decorators - Advanced**
* **Theory (15 min):** Decorators with arguments. Using `functools.wraps` for preserving metadata. Class-based decorators.
* **Hands-on (15 min):**
    * Modify `log_calls` to accept an argument (e.g., `log_level`).
    * Use `functools.wraps`.
* **Mini-Project:** Create a decorator `require_permission(permission_level)` that checks if a user has the required permission before executing a function.

**Day 21: Context Managers (`with` statement)**
* **Theory (15 min):** The `with` statement. `__enter__` and `__exit__` methods. `contextlib` module (`@contextmanager`). (Relate to Swift's `defer` or resource management patterns).
* **Hands-on (15 min):**
    * Create a custom context manager for a temporary file that cleans itself up.
    * Use `@contextmanager` decorator for a simpler context manager.
* **Mini-Project:** Implement a `Timer` context manager that prints the duration of the code block it wraps.

**Day 22: `functools` Module & Advanced Functions**
* **Theory (15 min):** `functools.partial` (partial application), `functools.lru_cache` (memoization). `map`, `filter`, `reduce` (briefly, as comprehensions are often preferred).
* **Hands-on (15 min):**
    * Use `partial` to create a new function from an existing one with some arguments pre-filled.
    * Apply `lru_cache` to a recursive function (e.g., Fibonacci) and observe performance.
* **Mini-Project:** Create a memoized version of a computationally expensive function (e.g., a factorial calculator).

---

### Phase 5: Concurrency & Testing (Days 23-28)

**Day 23: Concurrency - Threads & GIL**
* **Theory (15 min):** `threading` module basics. Creating and starting threads. `join()`. **Deep dive into GIL's impact:** I/O-bound vs. CPU-bound tasks. (Crucial contrast with Swift's threading model).
* **Hands-on (15 min):**
    * Write a simple I/O-bound task (e.g., fetching multiple URLs) using threads and observe concurrency.
    * Write a simple CPU-bound task (e.g., heavy calculation) using threads and observe the GIL's effect (no true parallelism).
* **Mini-Project:** Simulate a web scraper that fetches 5 different URLs concurrently using `threading`.

**Day 24: Concurrency - Processes**
* **Theory (15 min):** `multiprocessing` module. Creating and starting processes. `join()`. When to use processes over threads (for CPU-bound tasks). Inter-process communication (briefly: `Queue`, `Pipe`).
* **Hands-on (15 min):**
    * Rewrite your CPU-bound task from Day 23 using `multiprocessing` and observe true parallelism.
    * Experiment with a simple `Queue` for passing results between processes.
* **Mini-Project:** Implement a parallel image processing script that applies a filter to different parts of an image using multiple processes.

**Day 25: Asynchronous Programming (`asyncio`)**
* **Theory (15 min):** Introduction to `asyncio` (event loop, coroutines). `async def`, `await`. `asyncio.run()`. `asyncio.sleep()`. (Relate to Swift's `async/await` syntax and event loop concept).
* **Hands-on (15 min):**
    * Write a simple `async` function.
    * Use `asyncio.run()` to execute it.
    * Create multiple `async` tasks and run them concurrently using `asyncio.gather()`.
* **Mini-Project:** Create an `asyncio` program that simulates fetching data from multiple "API endpoints" concurrently.

**Day 26: Testing - `unittest`**
* **Theory (15 min):** `unittest` module. `TestCase` class. `setUp`, `tearDown`. Assertions (`assertEqual`, `assertTrue`, `assertRaises`). Running tests.
* **Hands-on (15 min):**
    * Write a `unittest.TestCase` for your `Calculator` class.
    * Add tests for `add` and `is_positive`.
* **Mini-Project:** Write unit tests for your `User` class's factory methods.

**Day 27: Testing - `pytest`**
* **Theory (15 min):** Introduction to `pytest` (simpler syntax, no class inheritance needed). Basic assertions. Fixtures (`@pytest.fixture`). Running tests.
* **Hands-on (15 min):**
    * Rewrite your `Calculator` tests using `pytest`.
    * Create a simple fixture.
* **Mini-Project:** Convert your `Bank Account` tests to `pytest` and use fixtures for setting up account objects.

**Day 28: Virtual Environments & Package Management**
* **Theory (15 min):** Importance of virtual environments (`venv`). Creating, activating, deactivating. `pip` for installing, uninstalling, listing packages. `requirements.txt`.
* **Hands-on (15 min):**
    * Create a new virtual environment for a project.
    * Activate it.
    * Install a common library (e.g., `requests`).
    * Generate a `requirements.txt` file.
* **Mini-Project:** Start a new Python project, create a `venv`, install `pytest`, and write a basic test for a new utility function.

---

### Phase 6: Review & Project (Days 29-30)

**Day 29: Comprehensive Review**
* **Theory (15 min):** Revisit all notes. Identify areas where you feel less confident. Focus on the distinctions between similar concepts (e.g., lists vs. tuples, class methods vs. static methods, threads vs. processes).
* **Hands-on (15 min):**
    * Solve a few mixed-topic coding challenges online (e.g., from LeetCode Easy/Medium, HackerRank).
    * Review your own mini-project code and refactor for clarity and Pythonic style.

**Day 30: Mini-Project: Command-Line Tool**
* **Theory (15 min):** Plan the architecture of a simple command-line tool. Think about how to structure it into modules, use classes, handle errors, and potentially incorporate concurrency for I/O.
* **Hands-on (15 min):**
    * **Project Idea:** A simple **"File Analyzer"** command-line tool.
        * Takes a directory path as input.
        * Counts files by extension (e.g., `.txt`, `.py`, `.jpg`).
        * Calculates total size of files.
        * (Optional: Use `multiprocessing` to count files in subdirectories in parallel).
        * (Optional: Use `argparse` for command-line argument parsing).
    * Start implementing the core logic, focusing on applying the concepts learned over the past 29 days.

---

**Tips for Success:**

* **Consistency is Key:** Stick to the 30 minutes daily.
* **Active Learning:** Don't just read; type the code, experiment, break it, fix it.
* **Leverage Your Experience:** Constantly ask yourself: "How would I do this in Swift?" and "What's the Pythonic way?" This comparison will accelerate your understanding.
* **Pythonic Style:** Pay attention to PEP 8 (Python's style guide). Tools like `flake8` or `black` can help.
* **Official Docs:** The official Python documentation is excellent.
* **Community:** Stack Overflow, Real Python, GeeksforGeeks are great resources.
* **Be Patient:** Some concepts (like the GIL or decorators) might take a bit longer to click, but your foundation will help.

---

## Summary

| Day | Date     | Topic                              | Key Concepts & Practice                                                   |
| --- | -------- | ---------------------------------- | ------------------------------------------------------------------------- |
| 1   | July 11  | Python Setup & Basics              | Install Python, print, variables, string basics, mini hello-world project |
| 2   | July 12  | Operators & F-Strings              | Arithmetic, comparisons, f-strings, basic calculator                      |
| 3   | July 13  | Control Flow                       | if-else, loops, break, continue, guessing game                            |
| 4   | July 14  | Lists & Tuples                     | List operations, tuple immutability, to-do list project                   |
| 5   | July 15  | Dictionaries & Sets                | dicts, sets, common methods, contact book project                         |
| 6   | July 16  | Functions & Arguments              | def, args, kwargs, defaults, calculate average function                   |
| 7   | July 17  | Comprehensions & Generators        | List/dict/set comprehensions, basic generator, Fibonacci sequence         |
| 8   | July 18  | Classes & Objects                  | Class, **init**, instance/class variables, bank account                   |
| 9   | July 19  | Inheritance                        | Parent-child classes, method overriding, animals example                  |
| 10  | July 20  | Polymorphism                       | Common interface, method overriding, shape example                        |
| 11  | July 21  | Class & Static Methods             | @classmethod, @staticmethod, factory pattern, validation example          |
| 12  | July 22  | Encapsulation & Properties         | Private attributes, @property, access control                             |
| 13  | July 23  | Error Handling Basics              | try-except, finally, zero division handling                               |
| 14  | July 24  | Custom Exceptions                  | Defining & raising exceptions, password validation                        |
| 15  | July 25  | File I/O Basics                    | Text file read/write, context managers, name list project                 |
| 16  | July 26  | Binary Files & OS Module           | shutil, os, file organization project                                     |
| 17  | July 27  | Modules & Packages                 | Imports, **init**.py, reusable code organization                          |
| 18  | July 28  | Iterators & Generators             | **iter**, **next**, yield, playlist iterator                              |
| 19  | July 29  | Decorators Basics                  | Simple function decorators, logging                                       |
| 20  | July 30  | Advanced Decorators                | Decorators with args, functools.wraps, permissions                        |
| 21  | July 31  | Context Managers                   | with statement, resource management, timer example                        |
| 22  | August 1 | functools & Higher Order Functions | partial, lru\_cache, map/filter/reduce                                    |
| 23  | August 2 | Concurrency with Threads           | threading, GIL, web scraping example                                      |
| 24  | August 3 | Concurrency with Processes         | multiprocessing, IPC, parallel image processor                            |
| 25  | August 4 | Asyncio Basics                     | async/await, asyncio.run, concurrent tasks                                |
| 26  | August 5 | Unit Testing with unittest         | TestCase, assertions, test bank account                                   |
| 27  | August 6 | Unit Testing with pytest           | Pytest syntax, fixtures, test coverage                                    |
| 28  | August 7 | Virtual Environments & Packaging   | venv, pip, requirements.txt                                               |
| 29  | August 8 | Comprehensive Review               | Code challenges, review weak spots, practice problems                     |
| 30  | August 9 | Final Mini-Project: CLI Tool       | File Analyzer: counts files, extensions, sizes, optional multiprocessing  |


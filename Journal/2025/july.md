# July 2025

---

## Tuesday, 1st July 2025

- PyCharm download, installation
- Verify the SHA 256 checksum
    - shasum -a 256 pycharm-2025.1.2-aarch64.dmg
- Python iterators
    - Added examples at
        - https://github.com/saurabh1088/python/blob/main/learnings/about_iterators.py

---

## Wednesday, 2nd July 2025

- Python iterators
    - Documented implementation of `Counter` @https://github.com/saurabh1088/python/blob/main/learnings/about_iterators.py
    - Added example for iterator with error handling for case going beyond limit.

```
What are some practical, real-world use cases where iterators in Python provide clear advantages? Please include brief code examples to illustrate each use case.
```

### TODOs
- [ ] Add an example for iterator to generate fibonacci numbers
- [ ] Document prompt

---

## Thursday, 3rd July 2025

- Prompt
- Added python generator examples
    - https://github.com/saurabh1088/python/blob/main/learnings/about_generators.py
- Added generator notes to QnA
    - https://github.com/saurabh1088/notes/blob/main/Python/QnA.md

```
Explain the practical, real-world advantages of using iterators in Python, providing at least three distinct use cases. For each use case, include:

A clear explanation of the problem that iterators help solve, highlighting why they are a superior solution compared to alternative approaches (e.g., loading all data into memory).

A brief, illustrative code example that demonstrates the use of iterators in that specific context.

A concise explanation of the code and how the iterator contributes to efficiency, memory management, or other benefits.

Focus on scenarios where iterators offer tangible benefits in terms of performance, resource consumption, or code elegance.
```

### TODOs
- [ ] Document prompt
- [ ] https://www.programiz.com/python-programming/generator

---

## Friday, 4th July 2025

- oAuth Revision

### TODOs
- [ ] Check URL Schemes in current project.
- [ ] Check auth implementation in current project.

---

## Saturday, 5th July 2025

- iOS Notes Revision
- Added QnA for NSCacheDelegate
- Added disadvantages for NSCache

### Prompts
```
I am designing an iOS application that is expected to serve millions of active users, implying high concurrency demands and strict performance requirements. I need an in-depth, technical explanation of **concurrency management in iOS, specifically within the Swift programming language context.**

Please cover the following aspects comprehensively:

1.  **Core Concurrency Primitives & Paradigms:**
    * **Swift Concurrency (`async/await`, `Task`, `Actor`):** Detail their underlying mechanisms, how they differ from older concurrency models (especially GCD's serial/concurrent queues), and the benefits they offer (e.g., compile-time safety, structured concurrency, improved readability). Discuss common pitfalls like actor re-entrancy and how to manage them.
    * **Grand Central Dispatch (GCD):** Explain its role for low-level concurrent operations, quality of service (QoS) classes, dispatch queues (serial vs. concurrent, sync vs. async), and their appropriate use cases in a large-scale app. How do `DispatchWorkItem` and `DispatchGroup` fit in?
    * **Operation Queues (`OperationQueue`, `Operation`):** Elaborate on their advantages for complex task dependencies, cancellation, and state management, providing scenarios where they might still be preferred over Swift Concurrency or raw GCD.

2.  **Addressing Concurrency Challenges at Scale:**
    * **Data Races & Thread Safety:** Beyond basic definitions, discuss advanced strategies for preventing data races in shared mutable state, especially across different concurrency mechanisms. Explain how actors provide isolation and when `nonisolated` is appropriate.
    * **Deadlocks & Livelocks:** How do these manifest in iOS apps, and what design patterns or debugging techniques can prevent them?
    * **Priority Inversion:** Explain its concept and how different QoS classes, or actor prioritization, mitigate this in a complex system.
    * **Resource Contention:** Strategies for managing access to limited resources (e.g., database connections, file handles, network bandwidth) efficiently under high load.
    * **Memory Management in Concurrency:** Discuss the impact of concurrent operations on memory footprint, avoiding memory leaks in asynchronous code, and considerations for large data sets.

3.  **Real-World Scenarios & Advanced Implementations for Million-User Apps:**
    * **High-Volume Networking:** How to handle thousands of concurrent network requests efficiently, including request prioritization, rate limiting, and robust error handling. Discuss `URLSession`'s role and advanced configurations for high-throughput scenarios.
    * **Complex UI Rendering & Animation:** Strategies for keeping the UI buttery smooth (60-120fps) even during heavy background processing, including offloading layout calculations, image decoding, and data transformations.
    * **Local Data Persistence at Scale:** Managing concurrent reads/writes to Core Data, Realm, or SQLite databases without blocking the UI or causing corruption. Discuss efficient background saving and merging strategies.
    * **Background Tasks & App Lifecycle:** How to effectively use background fetch, background processing tasks, and silent push notifications to pre-fetch or process data without impacting foreground performance or battery life. How does concurrency influence app lifecycle management (suspension, termination)?
    * **Cross-Process Communication (if applicable):** Briefly touch upon scenarios (e.g., App Extensions, Widgets) where inter-process concurrency considerations arise.

4.  **Performance Tuning & Debugging Concurrency Issues:**
    * **Xcode Instruments:** Deep dive into using `Allocations`, `Time Profiler`, `Leaks`, `System Trace`, and `Points of Interest` to diagnose and resolve concurrency-related performance bottlenecks, freezes, and crashes.
    * **Thread Sanitizer (TSan):** Explain its utility for detecting data races at runtime.
    * **Best Practices & Design Patterns:** Discuss common design patterns for robust concurrent systems (e.g., Producers/Consumers, Thread Pools, Message Queues) and when they apply in Swift.
    * **Testing Concurrency:** Strategies for writing effective unit and integration tests for asynchronous code to ensure correctness and stability under load.

Assume a strong understanding of basic Swift syntax and iOS app architecture. The goal is to gain practical, actionable knowledge to build a highly performant and stable iOS application for a large user base.
```

### TODOs
- [ ] NSCache vs URLCache which one to use for image caching
- [ ] Can one cache a rendered UI element?
- [ ] What is Actor reentrancy in Swift?

---

## Sunday, 6th July 2025

- Swift concurrency revision
- Added Swift Actor example 6
    - https://github.com/saurabh1088/swift-playgrounds/blob/main/Concurrency.playground/Pages/Actors.xcplaygroundpage/Contents.swift

### TODOs
- [ ] What is Livelocks?

---

## Monday, 7th July 2025

- Swift concurrency
    - Playground examples for Task API

---

## Tuesday, 8th July 2025

- Revision async/await
- Semaphores
    - unsigned int
    - changes are atomic
    - 2 operations it supports
        - wait() 
        - post() OR signal()
- Python's Global Interpreter Lock
    - Started
    - https://realpython.com/python-gil/

### TODOs
- [ ] What is mutex?
- [ ] Read https://realpython.com/python-gil/

---

## Wednesday, 9th July 2025

- Python
    - Global Interpreter Lock
        - Added markdown https://github.com/saurabh1088/notes/blob/main/Python/GlobalInterpreterLock.md

---

## Thursday, 10th July 2025

- Python
    - @staticmethod
        - Added examples at https://github.com/saurabh1088/python/blob/main/learnings/about_static.py
    - @classmethod
    - instance methods
        - Added examples at https://github.com/saurabh1088/python/blob/main/learnings/about_class_members.py

---

## Friday, 11th July 2025

- Prompt
```
As a seasoned Python architect with over two decades of hands-on experience in designing and implementing robust, scalable systems, please provide a deep dive into the nuanced differences between @classmethod, @staticmethod, and how they interact with class-level properties in Python.

Go beyond the basic syntax. I'm looking for:

Fundamental Conceptual Distinctions: Elaborate on the core philosophy behind each decorator. What problem does each solve, and why would one choose one over the other from an architectural standpoint?

Interaction with Class-Level Properties:

Clearly explain how both @classmethod and @staticmethod access and potentially modify class variables (which serve as static properties).

Discuss the implications of using cls.property_name versus ClassName.property_name within these methods, especially in the context of inheritance.

Real-World Scenarios and Justification: Provide compelling, comprehensive examples from typical project contexts where:

A @staticmethod is the unequivocally correct choice, explaining why it fits that specific utility or helper role.

A @classmethod is the ideal solution, particularly showcasing its power in factory patterns, managing class-level registries, or scenarios requiring awareness of the actual runtime class.

Interchangeability and Purpose: Explicitly state if and when these two method types are not interchangeable, emphasizing their distinct purposes and the pitfalls of misusing them.

Impact of Inheritance: This is crucial. Detail how inheritance affects:

The behavior of @classmethods (polymorphism through cls).

The behavior of @staticmethods (lack of polymorphism).

How class properties (static properties) are inherited by subclasses, and how method calls (both instance and class methods) correctly resolve to the most specific class property in the hierarchy.

The goal is to gain practical, architectural insights that go beyond simple definitions, enabling a clear understanding of when and why to employ each of these powerful Python features in complex, maintainable codebases.
```

- Added PnA to Python folder
    - https://github.com/saurabh1088/notes/blob/main/Python/PnA.md
- Added one PnA to clipboard
    - https://github.com/saurabh1088/notes/blob/main/Journal/clipboard.md
- Anaconda & Miniconda
    - https://conda.org/
    - https://www.anaconda.com/

---

## Saturday, 12th July 2025

- Python
    - Operators
        - walrus operator
            - https://www.datacamp.com/tutorial/python-walrus-operator
    - Added file https://github.com/saurabh1088/python/blob/main/learnings/about_operators.py
    - f-strings
        - Added examples : https://github.com/saurabh1088/python/blob/main/learnings/about_strings.py

```
Create a comprehensive and comparative list of operators that are either exclusive to Python or implemented in a uniquely Pythonic way. Highlight how these operators differ from or are absent in other mainstream programming languages such as C, Java, Swift, JavaScript, and others. Include practical examples, explanations of their purpose, and notes on whether equivalent functionality exists (or not) in those other languages.
```

---

## Sunday, 13th July 2025

- Prompts
    - Updated sheet at https://github.com/saurabh1088/notes/blob/main/misc/Prompts/Prompts.md
- Collections
    - Swift's lazy evaluation
        - LazySequence
        - LazyCollection
        - .lazy property
- Swift Sequence
    - Added playground file
        - https://github.com/saurabh1088/swift-playgrounds/tree/main/Swift/Sequence.playground

### Prompts
```
As a senior software engineer, your task is to provide an in-depth, comparative explanation of collections across these programming languages: Swift, Python, JavaScript, and Kotlin.
Go beyond the basics — focus on advanced usage patterns, performance considerations, and memory efficiency relevant to high-performance and large-scale applications.

Cover topics such as:

- Mutability and immutability of collections

- Typed vs untyped collections

- Collection algorithms and higher-order functions (e.g., map, filter, reduce)

- Lazy evaluation and iteration

- Thread safety and concurrent collection access

- Backing data structures (e.g., arrays vs linked lists, hash tables)

- Performance trade-offs and optimization strategies

- Real-world scenarios where collection design impacts app performance or scalability

Provide code examples and architectural insights for each language, and highlight similarities, differences, and language-specific idioms.
```

---

## Monday, 14th July 2025

- Swift's lazy evaluation
    - Updated example at
        - https://github.com/saurabh1088/swift-playgrounds/tree/main/Swift/Sequence.playground

- Python
    - Memory management
        - https://github.com/saurabh1088/notes/blob/main/Python/MemoryManagement.md


### Prompts
```
Create a step by step learning plan for Data Structures. Assume learners have some basic knowledge of programming but not
good understanding of data structures. Plan should be covering all required relevant topics. Preferably 30min each day.
Plan should consider hands on practice using Python as programming language or suggest any alternative if better suited.
Include references wherever applicable or needed for further learning. Include some practice programming tasks for cementing
concepts and gaining hands-on.
```

---

## Tuesday, 15th July 2025

- Data Structures
    - Abstract Data Types (ADTs) vs. Concrete Implementations
    - Updated https://github.com/saurabh1088/notes/blob/main/DataStructures/DataStructures.md
    - Big O Notation
        - O(1)
        - O(n)

---

## Wednesday, 16th July 2025

- Data Structures
    - Big O Notation
        - O(n²)
        - O(log n) - Logarithmic Time
        - O(n log n) - Linearithmic Time
    - Updated https://github.com/saurabh1088/notes/blob/main/DataStructures/DataStructures.md
    - Added examples at
        - https://github.com/saurabh1088/python/blob/main/projects/data_structures/big_o_concepts.py

### TODOs
- https://www.youtube.com/playlist?list=PLMCXHnjXnTnszR6YSo1tQK2BMr15cC9Zh


---

## Thursday, 17th July 2025

OFF

---

## Friday, 18th July 2025

- Data Structures
    - Revise binary search
    - Added example file
        - https://github.com/saurabh1088/python/blob/main/projects/data_structures/arrays/array_examples_one.py

### TODOs
- Check https://www.async-let.com/
- Check MCP Model Context Protocol
- Check https://modelcontextprotocol.io/introduction


---

## Saturday, 19th July 2025

- Coding practice
    - Arrays examples
    - Added swift examples and unit tests
        - https://github.com/saurabh1088/swift-programming/blob/main/Sources/swift-programming/Arrays.swift
        - https://github.com/saurabh1088/swift-programming/blob/main/Tests/swift-programmingTests/ArraysTests.swift

---

## Sunday, 20th July 2025

- Coding practice
    - Arrays examples
    - Updated swift examples and unit tests
        - https://github.com/saurabh1088/swift-programming/blob/main/Sources/swift-programming/Arrays.swift
        - https://github.com/saurabh1088/swift-programming/blob/main/Tests/swift-programmingTests/ArraysTests.swift
    - Update python examples
        - https://github.com/saurabh1088/python/blob/main/projects/data_structures/arrays/array_examples_one.py


---

## Monday, 21st July 2025

- A new beginning
    - BB

- Coding practice
    - Documented example
        - https://github.com/saurabh1088/swift-programming/blob/main/Sources/swift-programming/Arrays.swift

---

## Tuesday, 22nd July 2025

- Python
    - Revision Global Interpretor Lock
    - Python dictionaries
        - Added examples
            - https://github.com/saurabh1088/python/blob/main/learnings/about_dictionaries.py

---

## Wednesday, 23rd July 2025

- Python
    - Python dictionaries
        - Added examples
            - https://github.com/saurabh1088/python/blob/main/learnings/about_dictionaries.py

### Prompts
```
Explain why Python chose to make dictionaries ordered by default (as of Python 3.7+). What were the technical and functional benefits of this decision, and what specific problems did it address? Additionally, discuss any potential disadvantages or trade-offs introduced by maintaining insertion order in dictionaries.
```

---

## Thursday, 24th July 2025

- Python
    - Python dictionaries
        - Added examples
            - https://github.com/saurabh1088/python/blob/main/learnings/about_dictionaries.py

### Prompts
```
For a Python beginner looking to start with generative AI, what are the absolute essential Python concepts and libraries needed to understand and utilize pre-trained generative models (e.g., text generation, image creation) effectively?
```

```
As a Python developer interested in research and innovation in generative AI, what advanced Python concepts, specialized libraries, and architectural patterns are crucial for implementing novel generative models (e.g., custom GANs, VAEs, Transformers) and conducting experiments efficiently?
```

```
For an intermediate Python developer aiming to build and fine-tune generative AI models (e.g., LLMs, diffusion models), what are the critical Python aspects to master? Provide a structured overview covering foundational Python, essential data science libraries, deep learning frameworks, and specific Generative AI concepts, highlighting practical skills and best practices for model development.
```

---

## Friday, 25th July 2025

- Python
    - Mutability
        - Added example file
            - https://github.com/saurabh1088/python/blob/main/learnings/about_mutability.py
        - Added QnA for mutability
            - https://github.com/saurabh1088/notes/blob/main/Python/QnA.md

---

## Saturday, 26th July 2025

- Python
    - Mutability
        - Updated QnA for mutability
            - https://github.com/saurabh1088/notes/blob/main/Python/QnA.md
        - Added example at
            - https://github.com/saurabh1088/python/blob/main/learnings/about_mutability.py

---

## Sunday, 27th July 2025

- Python
    - Mutability
        - Added example at
            - https://github.com/saurabh1088/python/blob/main/learnings/about_mutability.py
        - Added QnA for dictionary hash table requirement
            - https://github.com/saurabh1088/notes/blob/main/Python/QnA.md

- AI
    - Computer Vision
        - Updated notes https://github.com/saurabh1088/notes/blob/main/AI/Reboot.md

### Prompts
```
Teach comprehensive computer vision concepts in AI, focusing on their application and relevance for a mobile app developer.

Emphasize:
- Fundamental computer vision techniques (image classification, object detection, segmentation, image preprocessing).
- Use of modern AI models and frameworks (e.g., TensorFlow Lite, Core ML, ONNX) suitable for mobile deployment.
- Strategies for integrating computer vision features into mobile apps, considering device constraints (on-device inference, edge/cloud trade-offs, performance optimization).
- Practical workflows: collecting/annotating datasets, training models, optimizing and deploying them to iOS and Android.
- Real-world mobile use cases: face recognition, barcode scanning, AR, document scanning, accessibility, etc.
- Guidance on available APIs/SDKs (Vision API, ML Kit, etc.).
- Common pitfalls, security/privacy considerations, and best practices for mobile computer vision apps.

Ensure the instruction is hands-on and example-driven, enabling software developers to translate computer vision concepts into tangible mobile app features.
```

---

## Monday, 28th July 2025

- AI
    - Computer Vision
        - Added file for topic
            - https://github.com/saurabh1088/notes/blob/main/AI/ComputerVision.md
        - Tensors

---

## Tuesday, 29th July 2025

- AI/Python
    - Added folder
        - https://github.com/saurabh1088/notes/tree/main/Python/AI
    - Tensors in Python
        - Added file
            - https://github.com/saurabh1088/notes/blob/main/Python/AI/Tensors.md
- AI
    - Computer Vision
        - Updated file
            - https://github.com/saurabh1088/notes/blob/main/AI/ComputerVision.md

### Prompts
```
Teach in-depth about the critical role of tensors in artificial intelligence, particularly in computer vision and machine learning systems. Explain:

What is a tensor?
Define tensors, their mathematical foundation, and how they generalize scalars, vectors, and matrices.

Why are tensors important in AI?
Discuss their role as the fundamental data structure for representing, storing, and manipulating numerical data in deep learning frameworks (e.g., TensorFlow, PyTorch).

How do tensors power model operations?
Illustrate how multidimensional data (images, audio, video, text, etc.) are structured as tensors, enabling complex computations (dot products, convolutions, batch processing).

Tensors in computer vision:
Show concrete mobile examples—such as how an RGB image is represented as a 3D tensor (height, width, color channels) and passed through neural networks for classification or detection.

Benefits of using tensors:
Explain efficiency gains for parallel processing (GPU/TPU), consistency in model training/inference across platforms, and support for automatic differentiation.

Hands-on exercises:
Include practical demonstrations on creating, manipulating, and visualizing tensors with popular frameworks for both training and deploying models on mobile devices.

End Goal:
Make the learner understand—at both a conceptual and hands-on coding level—how tensors are the backbone of modern AI, why mastering them is essential for developers in computer vision and AI-driven mobile development, and how they underpin nearly every operation in neural networks.
```

---

## Wednesday, 30th July 2025

- ReactNative
    - Revision
- Security
    - Static Application Security Testing (SAST)
    - Software composition analysis (SCA)
    - Interactive Application Security Testing (IAST)
    - Dynamic Application Security Testing (DAST)
    - Distroless images(Docker)
    - Threat Modelling
        - Added page
            - https://github.com/saurabh1088/notes/blob/main/security/ThreatModelling.md

### TODOs
- [ ] Static Application Security Testing (SAST)
- [ ] Software composition analysis (SCA)
- [ ] Interactive Application Security Testing (IAST)
- [ ] Dynamic Application Security Testing (DAST)
- [ ] Distroless images(Docker)

---

## Thursday, 31st July 2025

---

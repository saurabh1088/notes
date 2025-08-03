# Concurrency & Parallelism


## 1. Conceptual Definition

### 1.1 Concurrency
#### 1.1.1 Definition
- The ability of a system to handle multiple tasks (or units of work) seemingly at the same time, by structuring and managing access to shared resources.

#### 1.1.2 Examples
- A web server handling multiple client requests,
    - each in its own thread or coroutine,
    - where progress switches between tasks as resources allow.

### 1.2 Parallelism
#### 1.2.1 Definition
- The ability to actually perform multiple computations simultaneously, leveraging multiple processors/cores.

#### 1.2.2 Examples
- Running a data-processing operation split across all CPU cores, such that each core processes a distinct chunk in parallel.



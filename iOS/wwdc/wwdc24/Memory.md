#  Heap Memory

## Source
WWDC 2024
Analyze heap memory
https://developer.apple.com/videos/play/wwdc2024/10173/

Heap memory is used directly and indirectly by apps, and this is something which as a developer one can control and optimise.
- Heap memory is where App’s reference types are stored.
- Heap memory is memory allocated by malloc(), directly or indirectly
- Memory which provides most control to developer
- Heap memory is almost always dirty hence counted against app’s memory limit

## Topic covers below pointers
- Measuring Heap
- Dealing with transient memory growth
- Tracking persistent memory growth
- Fixing memory leaks
- Improving runtime performance


## HEAP

### What is Heap memory? Where is fits within app’s virtual memory?
When an app starts, it gets its own empty address space of virtual memory. When app launches, the system loads its main executable, linked libraries and frameworks and maps in regions of read-only resource from disk. While running, the app also uses stack areas for each thread’s local and temporary variables, with dynamic and long-lived memory getting placed in memory regions collectively known as heap.
The heap is not just one block of memory, it’s made up of multiple virtual regions as well. Each region is broken into individual heap allocations. Under the hood, each of these regions are made up of 16KB memory pages from operating system. Each allocation can be however bigger of smaller. Memory pages can be in three states :
- Clean
- Dirty
- Swapped.
Dirty and Swapped count towards app’s memory footprint. In majority of cases, heap will be responsible for majority of the app’s memory footprint. Heap allocations are ones created using functions like malloc(). One however doesn’t calls these directly, usually it’s the compilers or runtime which uses these functions a lot.
Using malloc() the memory allocated is :
- Having a lifetime which extends beyond the scope which allocated it, until explicitly called free()
- Minimum allocation is 16bytes, this means even if the requirement is 4byte, 16bytes will be allocated
Malloc has a debugging feature, MallocStackLogging, which records call stacks and timestamps for each allocation. MallocStackLogging can be enabled in Xcode via a checkbox in scheme’s diagnostics tab.

Tracking memory usage
- Xcode memory report : It shows app’s memory footprint over time
- Memory graph debugger : Captures memory graphs, which are snapshots of all allocations and references between them, with MallocStackLogging enabled, this includes backtraces of these allocations as well. It’s a great tool to focus on a specific allocation.
- Xcode command line tools like below can analyse macOS and simulator processes directly, or investigate already captured memory graphs.
    - leaks
    - heap
    - vmmap
    - malloc_history
- Instruments : Allocations template records the history of all allocations and free events over time, aggregating statistics and call-trees to help track these back to you code. Leaks instrument take periodic snapshots of app’s memory to detect memory leaks.


## TRANSIENT GROWTH
Memory spikes in an app are one type of transient memory growth, this kind of growth is bad because :
- It causes memory pressure and can force system to react, leading to termination of app.
- Long term effect can cause fragmentation or holes in heap memory regions
- Autorelease pools are common reason for temporary memory growth. Objective C uses these pools to extend object lifetimes for return values from functions. Autorelease pools keep these return values alive by delaying a release until later. Now Swift can also produce autorelease objects when it calls into frameworks that use of expose Objective C APIs. Threads usually have a top-level autorelease pool, but it’s not cleaned very often. This can matter a lot in case of loops where large number of objects get created. Every iteration of loop gets objected autoreleased into the same autorelease pool and they can live longer than necessary. In case of loop which is after loop is finished. The fix of this issue is to declare a local autorelease pool scope to narrow down lifetimes. This causes objects to released into new inner per-loop autorelease pool and released on each iteration. This lead to fewer object being accumulated.


## PERSISTENT GROWTH
Persistent growth is the memory which doesn’t gets deallocated. Persistent growth is when memory footprint for app keeps increasing overtime.
Mark generation feature in Allocations Instruments can break down the growth by timespan

## MEMORY LEAKS
Reachability : All memory in program should be reachable through non-weak references from somewhere to be used in future.
- Useful Memory : Reachable
- Abandoned Memory : Reachable, but never be used again
- Leaked Memory : Unreachable


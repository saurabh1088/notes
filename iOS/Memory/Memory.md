# Memory

Excerpts from wwdc video : iOS Memory Deep Dive
https://developer.apple.com/videos/play/wwdc2018/416/

## Why reduce memory?
When one talk about reducing memory, what it means is to reduce the memory footprint. An needs to have lesser memory footprint
so that
- It provides a better user experience
- App can launch faster
- App will stay in memory longer
- Other apps too can stay in memory longer

Reducing memory == Reducing memory footprint

## Memory Pages
In many operating systems as part of memory management, a memory page refers to a fixed-length contiguous block of memory 
managed by the operating system's memory manager. The size of this page can vary as per operating system, architecture etc.
These pages serve as a basic units of memory allocation.

## Memory Footprint
A memory page is given by system and it can hold multiple objects on heap. Some objects can span multiple pages. In iOS
typically pages are 16K in size. Pages can be of following type:
- Clean
- Dirty

Pages are clean when nothing is written on to them, if we write something then it's dirty.

### Memory usage of the app
Memory usage of the app = Number of Pages * Page size


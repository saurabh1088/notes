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
typically pages are 16KB in size. Pages can be of following type:
- Clean
- Dirty

Pages are clean when nothing is written on to them, if we write something then it's dirty. What this means in that when
memory is allocated, the allocated memory pages are cleab until some data is written onto those.

### Memory usage of the app
Memory usage of the app = Number of Pages * Page size

### Memory-mapped files
These are the files which are on disk but loaded into memory. Read-only files are always clean pages. The kernet manages
as they come on and off from disk to RAM. For example a JPEG file is stored on disk, but will be loaded onto memory to say
for display in app. So a 32KB JEPG image file when is memory-mapped will need two memory pages at the least. If say the JPEG
is 50KB then it will need four pages, where the fourth page will not be completely used, hence the fourth page can still
be utilized for other purpose.

### Typical Apps memory profile
Following are the segment of memory one finds in a typical apps memory profile
1. Dirty
2. Compressed
3. Clean

- Clean memory is the one which has data that can be paged out. These are memory mapped files.
- Dirty memory is any memory that has been written to by the app.

Apps memory footprint = Dirty memory + Compressed memory


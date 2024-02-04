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
- In iOS there is a memory compressor which takes unaccessed pages and squeeze those down to create more space. When those
pages are read then those will be decompressed again by compressor to read.

For example there is a dictionary in app which is being used for caching. Now, suppose it is using ten pages of memory
right now, but if this cached content isn't accessed for quite a while and the system needs some space, it can actually
squeeze it down into fewer pages. Now memory holding this cache is compressed and we save some space getting few extra
memory pages. When in future the cache is accessed again. memory will grow back.

Apps memory footprint = Dirty memory + Compressed memory

## Tools for profiling footprint

### Instruments
1. Allocations
    - Profiles the heap allocations made by app

2. Leaks
    - As name suggests, this will check memory leaks in process over time

3. VM Tracker
    - There is dirty memory and compressed memory, VM Tracker provides way to profile this.

4. Virtual memory trace

Xcode memory debugger under the hood uses *Memgraph* file format. These Memgraphs can also be used with command-line tools.
One can export the Memgraph from Xcode and analyse using command-line tools like *vmmap*

### Command line tool : vmmap
It gives a high-level breakdown of memory consumption in one's app by printing the VM regions that are allocated to the
process. It will print in details various memory like, amount of memory of region which is dirty, amount of memory which
is swapped(compressed in iOS). The swapped or compressed size given by *vmmap* is the size before compression.

### Command line tool : leaks
*leaks* tracks objects on heap which aren't rooted anywhere at runtime. If an object is in leaks, it is a dirty memory which
one can't free.

### Command line tool : heap
It provides all the information about object allocations in the process heap, it will list down all object allocations, the
class name for objects and the number of objects allocated, their average size and total size, it can help one identify:
- very large allocations
- lots of similar objects

### Command line tool : malloc_history

### Now which tool to pick?
|Creation|Reference|Size|
|---|---|---|
|Object Creation|References of object|How large is the object|
|Helps find backtrace for object|Helps to find what all is referencing to the object|Helps to realize size of the object|
|need to have malloc stack logging enabled|-|-|
|malloc_history|leaks|vmmap, heap|

## Images and implication over memory
One of the largest objects in an iOS App can be images, hence this needs a discussion over implications over memory.
Also about images, one of the important thing is to remember that the memory use is related to the dimensions of the image,
not its file size.

For example let's take an image of size 590KB which is of size 2048x1536 pixels. This image on disk is 590KB, but when loaded
in memory will become of size 2048x1536x4 Bytes which turns out to be approximately 12MB. This happens because on iOS the images
have following three phases:

Load -> Decode -> Render

- Load Phase : The 590KB image which is compressed format, is loaded into memory.
- Decode Phase : This converts image to a format which the GPU can read and here it is using 4 bytes per pixel calculation
becomes approximately 12MB, this is by SRGB format. SRGB is typically the most common format. One can go more rich formats
or less rich formats.

### Downsampling Images
In apps sometimes one has to downsample images. For example to use thumbnail images. If one uses UIImage to draw, then it
will have implications on memory usage, as the image will first get decompressed for transformation. Instead for downsampling
one should use *ImageIO* framework. *ImageIO* can actually downsample the image, and it will use a streaming API such that
one only pay the dirty memory cost of the resulting image. So this will prevent a memory spike.

### Best practices when dealing with Images
1. **Unload large resources which one can't see**
    Suppose in an app when a view opens it's showing an image. To show image, it has to be loaded into memory, now if for
    any scenario user has to go to a different screen, or lets say if some phone call comes in user jumps to attent that
    call and app goes to background. Now the image will still be in memory and app continues to use memory. So here it would
    be a good practice to unload large resources which user is not seeing at the moment. One can do this in two ways
        - One can use app life cycle notifications
        - UIViewController life cycle methods

2. **Let iOS pick the image format**
    Instead of using now deprecated UIGraphicsBeginImageContextWithOptions API, one should switch to UIGraphicsImageRenderer.
    UIGraphicsBeginImageContextWithOptions is always 4-byte-per-pixel format, whereas UIGraphicsImageRenderer will automatically
    pick the best format.

3. **For downnsampling instead of using UIImage, use *ImageIO***

## Stack vs Heap

|Stack|Heap|
|---|---|
|Region of memory used for static memory allocation|Region of memory used for dynamic memory allocation|
|Managed by the program itself|Need to be allocated/deallocated|
|Allocation is over contiguous blocks of memory||
|Called stack as allocation happens in the function call stack|It's a pile of memory available for a programmer to allocate/deallocate|
|LIFO||
|Managed automatically|Not managed automatically|
|Limited in size|Typically larger than stack memory|
|It is fast|Slower than stack|

### Stack Memory
Stack memory is a region within RAM(Random Access Memory) which is used for static memory allocation managed usually by program's
runtime environment, operating in a LIFO manner. Every time when a function is called, system allocates some stack memory
for the funtion. When a local variables is declared, more stack memory is allocated for that function to store that variable.
Such allocations make the stack grow downwards. After the function returns, the stack memory of this function is deallocated,
which means all local variables become invalid. The allocation and deallocation for stack memory is automatically done.
The variables allocated on the stack are called stack variables, or automatic variables.

## TODOs
- [ ] Watch https://developer.apple.com/videos/play/wwdc2016/416/
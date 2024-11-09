#  QnA

## 1. What are the common performance bottlenecks in iOS apps?
Following are some common performance bottlenecks in iOS App

### Main thread overload/blockage
Main thread in any iOS app has huge responsibilities for example it handles
- UI updates
- Events
- User interactions
If one performs any heavy duty tasks on main thread, immediately one notices impact on UI like UI might freeze or response
time increases. Accidently performing any networking related task on main thread can lead to very noticeable performance
issues and can make user experience extremely bad.

### Memory issues
- Memory leakage can lead to increasing memory footprint of the app.
- Caching too much data can lead to excessive memory usage and can lead to app termination.
- Using very large objects can lead to more memoy usage, large objects ideally should be optimised.

### UI Rendering
- Complex UI layouts and too much deep view hierarchies can lead to performance bottlenecks.
- Excessive drawing can lead to performance issues.
- Handling images especially large images if not handled efficiently. While loading large images ideally those should only
be loaded when needs to be displayed asynchronously. Preferably one should use smaller images to display unless image is
required to be displayed in large format. Size manipulation if can be done on backend is preferred.
- Animations should be handled carefully and stopped once view dissappears else it leads to performance issues.

### App launch time
- Minimise work required to get app to start.
- Too many API calls during startup or animations lead to impression of app taking long to start.


## 2. How to approach performance optimization in an iOS App?

### Profile using Instruments
Instruments in Xcode should be used to profile app using following options in it
- Time Profiler
- Allocations
- Leaks
- Energy Log

### Track CPU and Memory Usage
Track the CPU and Memory usage for the app using Xcode or Instruments. High CPU usages areas can be investigated.

### UI optimization
- Reduce view hierarchy complexities as too deep nested view hierarchies can slow down rendering.
- Complex autolayout constraints can lead to slowness due to time consuming autolayout constraint resolving.
- Large data sets while shown in a tableview should be optimised to be loaded in batches and lazy loading should be used.

### Data handling
- Ensure data is fetched in batches when data set is huge, this avoids scenario of requesting a huge data set in one go
which can slow down app and consume huge amount of memory.
- Frequently used data which doesn't changes should be cached, this can avoid repeated network calls and reduce network
traffic.
- JSON parsing should be used utilising Codable protocol, it's native, efficient and fast.

### Handling Media
- Appropriate size images should be used, for example to show image in a tableview cell where small size is appropriate,
consider using smaller size images than downloading full size images.
- Always lazy load images and download only if those are required to be shown.
- All this while do maintain that any loading of images from remote needs to be asynchronous operation.

### Optimize background work
- Any background work should be necessary and one should avoid any prolonged background tasks. Running too many background
tasks or longer running ones can lead to CPU usage and battery drainage.
- Timers should be invalidated when not in use.
- Location services should be requested only when required, and one should see possibility to use a lower accuracy setting
if that meets requirement.

### Optimize animations
- Use hardware accelerated properties. Properties like `opacity`, `position`, `transform`, and `bounds` are Core Animation
optimized properties and these are optimized for smooth animations.
- Limit animations as they lead to complexity and performance load.
- Offload animations to Core Animation, and use the shouldRasterize property on complex layers to cache rendered content
as a bitmap

### Optimize app launch time
- Ensure app loads fast and is not doing any long running processes at the begining.
- Welcome screen animations look cool but increase app launch times, those should be designed and used sensibly. Consider
loading any required resource while animation is playing to cut down total launch time.
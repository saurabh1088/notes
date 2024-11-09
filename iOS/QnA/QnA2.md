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

### App launch time
- Minimise work required to get app to start.
- Too many API calls during startup or animations lead to impression of app taking long to start.

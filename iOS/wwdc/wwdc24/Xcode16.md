#  Xcode 16

https://developer.apple.com/videos/play/wwdc2024/10135/
What’s new in Xcode 16

- Editing
    - Code completion through trained model over Swift language and apple specific SDKs.
        - It used surrounding context to provide better suggestions
        - Available when running Xcode 16 with macOS Sequoia

- Swift 6 comes with great concurrency features which turns data races from runtime issues to compile time ones.

- Xcode 16 Build Settings
    - Swift Compiler - Upcoming Feature
        - Here one can configure upcoming compiling features one at a time.


- Previews
    - @Previewable MACRO : New
    - PreviewModifier
    - Previews are faster than ever


- Build
    - Explicit modules
        - Improved parallelism
        - Better diagnostic
        - Faster debugging
        - Explicit modules are on by default for C and C++. For Swift it is an Opt in feature
        - Top opt-in for Swift, one needs to access Explicitly Built Modules in Project settings
        - Now one can also proceed with the build without having to wait for Swift Package Manager’s package resolution to complete.
        - Three phases
            - Scan
            - Build Modules
            - Build Source
        - One gets a much better breakdown of one’s build


- Thread Performance Checker
    - Disk write diagnostics : NEW
    - Launch diagnostics : NEW
    - In Xcode’s organiser, one can see the slowest code paths in launch diagnostics for customer devices.


- Unified Backtrace View


- Testing
    - Swift Tests
    - One can tag multiple tests which then Xcode will group together in organiser to show together, also one can then run those tests together.
    - Tags can be used to include or exclude any tests from test plan

- Profile
    - Flame Graph


https://developer.apple.com/videos/play/wwdc2024/102/
Platforms State of the Union


Text Editing
Gemoji
Image Playground

TODO:
Check build timelines to see where time is consumed a lot.
nonisolated
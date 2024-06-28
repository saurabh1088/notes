#  Swift

_Swift 6 comes with great concurrency features which turns data races from runtime issues to compile time ones._

## Source
What’s new in Swift
https://developer.apple.com/videos/play/wwdc2024/10136/


- Added platform support for Linux Fedora and Debian

- SourceKit LSP
    - Adapted in 
        - VSCode 
        - Emacs
        - Neovim & more

- Cross compilation
    - Compile on one environment and execute on different. 
    - Compile and build for macOS and run on, for example, iPad.
    - Cross compilation at present is not possible from macOS to Linux

- Foundation + swift-corelibs-foundation = swift-foundation introduced last year.

- Swift Testing : ✨NEW THIS YEAR
    - New Framework introduced

- Xcode build
    - Explicitly built modules
        - Can be enabled in Xcode project settings

- Swift Language Updates
    - Noncopyable types
        - All swift types are copyable by default. Noncopyable suppress this default copyablity
    - Embedded Swift
        - New subset of language.
    - C++ interoperability
    - Typed throws
        - func someThrowingFunction() throws(CustomError).
        - Typed throws lets one specify the error type.

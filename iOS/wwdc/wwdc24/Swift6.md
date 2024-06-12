#  Swift

Swift 6 comes with great concurrency features which turns data races from runtime issues to compile time ones.

https://developer.apple.com/videos/play/wwdc2024/10136/
What’s new in Swift

Added platform support for Linux Fedora and Debian
SourceKit LSP : Adapted in VSCode, Emacs, Neovim and more

Cross compilation : Compile on one environment and execute on different. Compile and build for macOS and run on for example iPad.
Cross compilation is possible not from macOS to Linux

Foundation + swift-corelibs-foundation = swift-foundation introduced last year.

Swift Testing : New Framework introduced

Xcode build :
Explicitly built modules : Can be enabled in Xcode project settings

Swift Language Updates
- Noncopyable types : All swift types are copyable by default. Noncopyable suppress this default copyablity
- Embedded Swift : New subset of language.
- C++ interoperability
- Typed throws : func someThrowingFunction() throws(CustomError). Typed throws lets one specify the error type.

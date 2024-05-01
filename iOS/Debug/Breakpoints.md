# Breakpoints

- Source file breakpoints
    - Line breakpoint (applied in gutter)
    - Column breakpoints(introduced with Xcode 13)
        Column breakpoint is very useful for scenario where there are multiple
        nested closures and one needs to apply breakpoint to one of those.
- Symbolic breakpoints
    - These are breakpoints on function names
    - Can be useful when one doesn't have access to source file.
- Runtime issue breakpoints
    - Xcode records a backtrace and shows it.

// TODO: Check latest on this and confirm
LLDB consists of two compilers
- Clang for Objective C
- Swift compiler
What's REPL

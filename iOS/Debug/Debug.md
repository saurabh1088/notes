#  Debug

## LLDB

LLDB stands for *low level debugger*. It's the debugger componenet of LLVM project.
LLDB is the standard debugger in Xcode.

## LLDB Commands

### help
List down all commands available

### thread backtrace
Gives stacktrace at the execution point, can be helpful to understand the call trace
leading to the point at which the command was executed.

### bt
Same as *thread backtrace*

### thread list
Prints list all threads.

### e <variable>
Prints the variable. Note : angular brackets are not required.

### frame variable OR fr v
Displays local variables in the current stack frame.

### type lookup


// TODO: Check latest on this and confirm
LLDB consists of two compilers
- Clang for Objective C
- Swift compiler

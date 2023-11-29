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


## Examining Data

*These commands below all can be used to examine data however these don't exactly
do the same thing*

- frame variable (fr v)
- expression (p)
- expression -O (po)

### The frame variable command

- This can be also run as shortened form as *fr v*
- This command pretty much gives Xcode variables view.
- It lets us look at local variables.
- One can specify a variable and it will let us look at only that variable.

### The expression command

- This can be also run as shortened form as *p*
- Used to run expressions, for example this can run simple arithmatic commands.
- One can use previous results and do further processing on those.

### The expression -O or po command

- This can be also run as shortened form as *po*
- Can create object and print their description printed out.


|frame variable|expression|expression -O|
|---|---|---|
|does not runs code|runs code|runs code|
|uses LLDB formatters|uses LLDB formatters|runs some extra code behind the scenes to format|

The *po* command follows a in-process formatting model where
- Data and formatter live together and writter with same language
- Has easy access to object model
- One need to be careful to not alter state of program
- Swift Playgrounds follows a in-process formatting model

Protocols for Swift in-process formatting
- CustomStringConvertible
    - Tells how to print object as a string representation
- CustomDebugStringConvertible
    - It's a debugger specific representation of object.
- CustomPlaygroundQuickLookable
    - Specifically for playground to provide rich representation
- CustomReflectable
    - Allows vending an entirely custom children hierarchy
    - Using this one can tell debugger to enable it to see how object is made of, i.e. what's structure of object.
    
These protocol conformances can be added at runtime as well through expression command.



// TODO: Check latest on this and confirm
LLDB consists of two compilers
- Clang for Objective C
- Swift compiler
What's REPL

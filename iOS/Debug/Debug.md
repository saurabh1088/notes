#  Debug

## LLDB

LLDB stands for *low level debugger*. It's the debugger componenet of LLVM project.
LLDB is the standard debugger in Xcode.

## LLDB Commands

### run
Start or if not running then re-start the code being debugged.

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
Displays all local variables in the current stack frame.

// TODO : Confirm this command (type lookup) if it's valid
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
- This is not compiling the code so it is fast, but it won't be able to work in 
case of say for e.g. computed properties
as computed property will need code to be run.
- This will be able to perform better at dynamic type resolution without needing
to explicit casting compared to p and po commands.

### The expression command

- This can be also run as shortened form as *p*
- Used to run expressions, for example this can run simple arithmatic commands.
- One can use previous results and do further processing on those.
- Result of each expression are given names like $R0, $R1 and so on.

### The expression -O or po command

- This can be also run as shortened form as *po*
- Can create object and print their description printed out.
- Can evaluate arbitrary expression, it anyways is an alias for command expression


|frame variable|expression|expression -O|
|---|---|---|
|does not runs code|runs code|runs code|
|uses LLDB formatters|uses LLDB formatters|runs some extra code behind the scenes to format|
|Data formatters|Data formatters|Object description|
|Not full access to language|full access to language|full access to language|
|Iterative dynamic type resolution|Dynamic type resolution only once|Dynamic type resolution only once|

The *po* command follows a in-process formatting model where
- Data and formatter live together and written with same language
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


## How LLDB works

Compiler compiles the source code to generate the machine code. In doing so it also
leaves breadcrumbs for the debugger so that an address can be mapped to source file,
line number etc. These breadcrumbs are called debug-info. Debug info on apple
systems is stored in object files. For archiving and distribution, debug info can
be linked into .dSYM bundles. The debug info linker is called *dsymutil*

LLDB can map to source path using below command

```
settings set target.source-map prefix new
```

## Breakpoints

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

#  Debug

## LLDB

LLDB stands for *low level debugger*. It's the debugger componenet of LLVM project.
LLDB is the standard debugger in Xcode.

## LLDB Commands

### run
Start or if not running then re-start the code being debugged. When control pauses over breakpoint and *run* command is
executed on *lldb* then it will run the application again.

### help
List down all commands available

### thread backtrace
Gives stacktrace at the execution point, can be helpful to understand the call trace leading to the point at which the
command was executed.

### bt
Same as *thread backtrace*

### thread list
Prints list all threads.

### e <variable>
Prints the variable. Note : angular brackets are not required.

### frame variable OR fr v
Displays all local variables in the current stack frame.

### type lookup <Type>
Prints information about the type.
For example for type : https://github.com/saurabh1088/SwiftUI/blob/main/SwiftUILearnings/Debug/DebugViewModel.swift one
can execute below command.
```
type lookup DebugViewModel
```

### lldb
*lldb* itself is a command which can be run in terminal on Mac to start a debug session.
Once the session is open then one can use commads to import for example crash logs to analyse those.

## Examining Data

*These commands below all can be used to examine data however these don't exactly do the same thing*

- dwim-print
- frame variable (fr v)
- expression (p) (IMP : THIS IS NOW ALIASED AGAINST COMMAND : *dwim-print*)
- expression -O (po) (IMP : THIS IS NOW ALIASED AGAINST COMMAND : *dwim-print*)

### The frame variable command

- This can be also run as shortened form as *fr v*
- This command pretty much gives Xcode variables view.
- It lets us look at local variables.
- One can specify a variable and it will let us look at only that variable.
- This is not compiling the code so it is fast, but it won't be able to work in case of say for e.g. computed properties
as computed property will need code to be run.
- This will be able to perform better at dynamic type resolution without needing to explicit casting compared to p and po commands. (IMP : See TODOs no. 1)

### The expression command

- Used to run expressions, for example this can run simple arithmatic commands.
- One can use previous results and do further processing on those.
- Result of each expression are given names like $R0, $R1 and so on.

### The expression -O (DOESN'T WORKS NOW)

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

Compiler compiles the source code to generate the machine code. In doing so it also leaves breadcrumbs for the debugger
so that an address can be mapped to source file, line number etc. These breadcrumbs are called debug-info. Debug info on
apple systems is stored in object files. For archiving and distribution, debug info can be linked into .dSYM bundles.
The debug info linker is called *dsymutil*

LLDB can map to source path using below command

```
settings set target.source-map prefix new
```


## Using po command to print variable, but seems like Xcode take too long to process, why so?
Because *po* compiles code dynamically to evaluate expressions, it takes more time to evaluate your variable and log it to
the console.
To reduce timing issues, use *v* to log variable values instead.
Also it's not just that *po* command is slow, it previously used to just print the address if *CustomStringConvertible*
was not implemented. But in latest releases of *lldb* Apple has implemented command *dwim-print* and aliases for both
*p* and *po* are re-defined to *dwim-print* command.

NOTE: As of Swift 5.9 *po* and *p* both now provide faster variable inspection.
Source : https://www.swift.org/blog/whats-new-swift-debugging-5.9/


## TODOs

- [ ] 1. As per example at below link it appears this point(_This will be able to perform better at dynamic type resolution without needing to explicit casting compared to p and po commands._) is no longer valid, need to explore more. 
https://github.com/saurabh1088/SwiftUI/tree/main/SwiftUILearnings/Debug
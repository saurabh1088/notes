#  Explicitly Built Modules


## Source
Demystify explicitly built modules
https://developer.apple.com/videos/play/wwdc2024/10171/


## Explicitly built modules
- New way Swift and Clang modules are built in Xcode.


## About Modules
Modules are units of code distribution describing the interface of a library or a framework. For example all the Swift files for a target or a framework are a single module.
Swift compiler takes the external interface and summarises it into a textual .swiftinterface file which contains just the interface. This is unlike Objective C, or C family of languages, where interface for module is hand written.
Modules allow compiler to share parsing of interfaces between source files. This is done by compiling each module in isolation into a binary file to be read by compiler when compiling project sources, then importing the public interfaces of that module whenever it is referenced. In Swift, this compiled form is represented as *.swiftmodule file. In clang this is represented as *.pcm (pre-compiled module file)
For example where say in a file the compiler encounters the import `import UIKit`, then it first finds UIKit’s module Map in the SDK, then it finds the compiled .pcm file for UIKit. What happens if this file is not present?


## Implicitly build modules
In an implicitly build modules, the compilers coordinate among themselves to manage building modules without the rest of Xcode being aware of their existence. This is how Swift and Clang build modules since they were introduced.
Using implicitly built modules, where a project has Swift, Objective C and C code, build contains many long-running tasks. Now during compilation process each compiler begins compilation process and may discover a module and will build the module if it reaches there first or will load the module If it’s already present. With implicitly built modules one can end up with situations where one compilation task is implicitly building the module which another compilation task which also need same module is blocked, waiting for the module to be built (compilations tasks here are being referred to compiling source files as per diagram show from same compiler : TODO confirm this). This can happen across the different parts of the build.

With Xcode 16 this behaviour changes with explicitly built modules. Xcode with explicitly build modules, coordinates with compilers to discover and build modules. Explicitly built modules takes the implicit work of building modules and lifts it up into explicit build system tasks. In order to do this Xcode splits up compilation of each source file into three separate phases.
- Scan
- Build Modules
- Build Source
Xcode starts of with scanning each source code file and building a module map graph for the entire project and even sharing modules across targets. Along with constructing the module graph, Xcode also starts dispatching module compilation tasks. These compilation tasks are explicit tasks in build log which are directly provided with the compiled module they depend on. Finally the original compilation tasks are performed which is building the source code which are modified to add compiled modules they depend on. Now with this explicit built modules, the build timeline view contains explicit
- scan tasks
- module compile tasks
- And source file tasks
With all of this taking significantly less time than before.

## What is the Benefit of explicit build modules over implicit build? TODO : Explore and expand on this
- There are execution lanes when Xcode builds an app or code. These execution lanes perform compilation process and other tasks. With implicit built modules several compilation tasks are waiting while also occupying the execution lane till the modules they depend upon are available. This leads to many execution lanes occupied, even though the compilation tasks in those are waiting state. With explicit built modules, as modules are built before the compilation of source code starts, the execution lanes are more efficiently used. This is because now one avoids filling execution lanes with tasks which are not ready to run.
- Reliable builds
- Deterministic sharing of modules
- Clean build now re-builds all modules
- More efficient builds as build system is responsible for scheduling
- Build system can pass modules to debugger, speeding startup. In implicit built module system, Xcode build and the debugger build both have completely separate module graphs. With explicitly built modules, debugger utilises the same module graph and built modules, like for when evaluating expressions like `p` or `po`


In Xcode 16, explicitly built modules are used for all C and Objective C code. This can be enabled for Swift for preview. To enable, select project’s build settings and search `Explicitly Built Modules` in the search box and set it to Yes.

In build logs one will see a lot of scan tasks. Followed by Module built tasks. One may see a module being built multiple times, which may happen if it’s being used in multiple targets with different requirements. In this case one will see the module with different hashes in the logs. This duplicity could be avoided by making build setting uniform across projects.



TODO:
- [ ] New this year 2024 FinanceKit
- [ ] New this year 2024 AccessorySetupKit
- [ ] New this year 2024 Contact Access Button
- [ ] https://developer.apple.com/videos/play/wwdc2024/10147
- [ ] https://developer.apple.com/videos/play/wwdc2024/10145


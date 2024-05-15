# Dependency Manager

_The role of a dependency manager is to automate the process of downloading and building all of the dependencies for a project, and minimize the coordination costs associated with code reuse._

## Swift Package Manager

### What is Swift Package Manager?
Swift Package Manager is a tool which manages distribution of source code, enabling easy sharing and re-use of code.

### What is a package?
A package consists of Swift source code files along with a file named *Package.swift* This Package.swift file is known as
manifest file or package manifest.

### What is a package manifest file and it's importance?
*Package.swift* file in a Swift package is known as package manifest. Every Swift package needs to have this package manifest
file. This package manifest is what defines the package's name and it's dependencies.

### How to build a package?
One can use below command
```
swift build
```

### What is a Dependency Hell?


Official documentation : https://github.com/apple/swift-package-manager/blob/main/Documentation/README.md

## Carthage
Carthage is probably the simplest way to add dependencies to project. Carthage builds and adds dependencies without
modifying any project files or structure.

### How to use Carthage?
Carthage should be installed on system. Having done that, one needs to add a *cartfile* in the directory where *.xcodeproj*
or *.xcworkspace* files reside.

## Cocoapods
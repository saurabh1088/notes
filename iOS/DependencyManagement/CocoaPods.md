# Cocoapods

_The role of a dependency manager is to automate the process of downloading and building all of the dependencies for a project, and minimize the coordination costs associated with code reuse._

## What is CocoaPods?
- CocoaPods is a dependency manager for Swift and Objective C projects.
- CocoaPods is used to automate the process of integrating third party libraries into Swift or Objective C projects.
- CocoaPods makes it easier to manage a project's dependencies and compatibility.
- CocoaPods is built with Ruby.


## pod install
- `pod install` is used to install new pods in project
- `pod install` will be used first time while retrieving pods for a project
- `pod install` will be used every time one edits `Podfile` to
    - add a pod
    - update a pod
    - remove a pod
- `pod install` updates `Podfile.lock` file every time it is run with pod version it has installed
- `pod install` resolves versions only for pods not listed in `Podfile.lock` file
    - For pod listed in `Podfile.lock` it simply uses the version listed there
    - For pod not listed in `Podfile.lock`, it install version as described in `Podfile`

### When should one run `pod install`
One should run `pod install` when
- 1. During Initial Setup
    - First time when a project is setup up for using CocoaPods.

- 2. When a repo is cloned
    - First time when a repository is cloned, `pod install` is required to get all dependencies.

- 3. Added a Pod
    - Every time one updates `Podfile` such that a pod is added.

- 4. Updated a Pod
    - Every time one updates `Podfile` such that a pod is updated for version or anything else.

- 5. Removed a Pod
    - Every time one updates `Podfile` such that a pod is removed.

- 6. Pulling changes on repo
    - Every time one takes a pull on repository such that it shows updates on `Podfile` or `Podfile.lock`.

- 7. Updating CocoaPods
    - If one updates CocoaPods to newer version, it is best practice to run `pod install` once.


## pod spec file
A pod spec file is a specification file used by CocoaPods to describe a framework or library. Pod spec file is a ruby file.


## How to updated a pod which is pointing to a branch and the branch has got new commits?
```
pod update PodNameToBeUpdated
```

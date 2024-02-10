# Android

## Kernel
Android is based on Linux Kernel, it's Android platform's foundation.

## Platform Architecture
Android Platform architecture consists of
1. Linux Kernel
2. Hardware Abstraction Layer
3. Android Runtime | Native C/C++ Libraries
4. Java API framework
5. System apps

## Languages
Languages one can use for developing an Android App:
- Kotlin
- Java
- C++

## App Compiled Output
An Android App is compiled and the output could be one of the following:
1. APK
2. Android App Bundle

## Security Sandbox
- An Android App on device runs in an isolated environment which is called as security sandbox. This security sandbox for apps
is protected by host of Android security features. 
- Each app in Android acts as a different user having a unique Linux user ID. This Linux user ID is assigned by sytem to each app. 
This ID system will used to give file permissions.
- Every Android App runs in its own Linux process. Lifecycle of this process is managed by Android system. Each process has
its own virtual machine, so every app runs in isolation from other apps.

## Principle of Least Privilige
Each Android app by default will get only the priviliges which require it to do its work and not more than that. This limits
apps permissions and access to only those resources and capabilities which are necessary for the app's functionalities.

## App Components
Essesntial building blocks for an Android App are termed as App Components.
1. Activities
2. Services
3. Broadcast receivers
4. Content providers

### Activity
An Activity in Android represents a single screen with user interaction.

## TODOs

- [ ] Can two apps in Android share data? If yes then how?
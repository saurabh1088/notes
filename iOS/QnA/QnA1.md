#  QnA

## 1. Explain iOS Architecture.

iOS Architecture consists of four layers as shown in below diagram.

![iOS Architecture](resources/ios_architecture.png "iOS Architecture")

### Core OS

At the core of iOS sits XNU Kernel.
This layer is directly on top of device's underlying hardware. This layer is responsible
for basic operating system services like

- Memory management
- Handling file system
- Threading and concurrency
- Low level networking
- Access to external accessories
- Security & Encryption features like Secure Enclave
- Device drivers helping communicate with harware components like CPU, GPU, storage etc.
- Components for power management
- Inter Process Communication (IPC) 

Core OS includes below frameworks and more

- Core Bluetooth Framework
- External Accessories Framework
- Accelerate Framework
- Security Services Framework
- Local Authorization Framework

### Core Services

- GCD
- iCloud Storage
- In-app purchase

Core Services includes below frameworks and more

- Address Book Framework
- Cloud Kit Framework
- Core Data Framework
- Core Foundation Framework
- Core Location Framework
- Core Motion Framework
- Foundation Framework
- HealthKit Framework
- HomeKit Framework
- Social Framework
- StoreKit Framework

### Media Services

This layer helps in handling audio, video and graphics.

Media Services includes below frameworks and more

- ULKit Graphics
- Core Graphics Framework
- Core Animation
- Media Player Framework
- AV Kit
- Open AL
- Core Images
- GL Kit


### Cocoa Touch

This is the application layer, this functions as interface to users and includes
touch and motion capabilities.

Cocoa Touch includes below frameworks and more

- EventKit Framework
- GameKit Framework
- MapKit Framework


## 2. What is UIViewController?

UIViewController in UIKit is responsible for managing view hierarchy for the app.


UIViewController is subclassed and inherited viewcontrollers are created to manage
an app's view hierarchies. One doesn't need to create instances of UIViewController
directly.

As UIViewController inherits from 

### Responsibilities of UIViewController

- Updating the views it manages
- Handling user interaction events
- Resizing views and managing layout
- Coordinating with other objects and other viewcontrollers in app


### UIViewController as responder

- UIViewController inherits from UIResponder. 
- So techincally a UIViewController object is also a UIResponder object.
- UIViewController objects are part of responder chain.
- When none of the UIViewController's views handle an event, then UIViewController
has option of handling it or passing it to superview.

### UIViewController placement in responder chain

UIViewController object in responder chain is inserted in between the viewcontroller's
root view and root view's superview.


### UIViewController's view property

- Job of UIViewController is to manage a view hierarchy.
- The root view of this hierarchy is stored in UIViewController's view property.

### What is root viewcontroller?

The viewcontroller owned by the window is the app's root viewcontroller.

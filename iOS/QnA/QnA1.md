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


### UIViewController's *view* property

- Job of UIViewController is to manage a view hierarchy.
- The root view of this hierarchy is stored in UIViewController's view property.
- UIViewController will load *view* lazily, i.e. when the view property is accessed
for the first time then only viewcontroller's views are loaded or created.
- Initially the value of *view* is nil. If one accesses this property when value is
nil, then viewcontroller will automatically call loadView() method and return the
resulting view. 

### What is root viewcontroller?

The viewcontroller owned by the window is the app's root viewcontroller.


## 3. Can one access UIViewController's *view* property?

Yes one can access UIViewController's *view* property, the only caveat to accessing
it is that if this property have value nil then accessing this property can cause
the view to be loaded automatically, as the viewcontroller will automatically call
loadView() method and return the resulting view.

Hence safe way to access *view* property is to use property *isViewLoaded* which
tells if the view is currently in memory or not. Accessing *isViewLoaded* will not
force calling loadView() method or trigger loading of view.


## 4. How do you specify *view* for a UIViewController?

Following are ways to specify *view* for a UIViewController subclass. We mention
subclass here as UIViewController is rarely instantiated and any app will subclass
it to provide implementation and then provide *view* using one of the below approach.

All three approaches mentioned below have same result which aims at creating views
for viewcontroller and expose the hierarchy through *view* property.

### Storyboards

### NIB Files

### loadView()

## 5. Why is it important for URLSession's dataTask method completion handler to update UI always on DispatchQueue.main block?

The completion handler associated with URLSession's dataTask method gets called on
a different queue than the one created the task in first place so any work in the
completion handler updating UI should be explicitly placed on the main queue.


## 6. What are @IBDesignable and @IBInspectable in Swift?

TODO : Hands on with IBDesignable and IBInspectable
TODO : Read throught and try out https://nshipster.com/ibinspectable-ibdesignable/

### @IBDesignable

@IBDesignable is an attribute which when is applied to a UIView or NSView subclass,
tells Interface Builder in Xcode to render the view directly in the canvas. This
allows seeing how that custom views will appear without building and running the
app after each change.

### @IBInspectable

XIB/NIB and Storyboards have an old feature - user-defined runtime attributes. These
were accessible from identity inspector in Xcode's Interface builder.
@IBInspectable properties provides new access to this old feature. 

@IBInspectable is an attribute which help exposing a property to Interface Builder
in Xcode. When a property is marked with @IBInspectable attribute, then it becomes
editable in Attributes inspector within Interface Builder in Xcode. This implies that
one can set or adjust it from Interface Builder, without writing code.

Example :
https://github.com/saurabh1088/uikit/blob/main/UIKitLearnings/UIKitLearnings/BezierPaths/RectangularView.swift

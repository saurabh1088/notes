# Core Data


## What is Core Data?
Simply stating : *Core Data is a FRAMEWORK*

Core Data is first and foremost a framework for managing an object graph.

Core Data can help to 
- Save application’s permanent data(offline usage)
- Cache temporary data
- To add Undo functionality
- Sync data across multiple devices(using CloudKit working with CoreData)


## Features from bird's eye view
### 1. Persistence

Core Data as mentioned can be used for data persistence by opting for a persistent store. The default store is SQLite.
Core Data proves abstraction over objects mapping to persistent store. This makes easy to save data without having to administer
database directly.

### 2. Undo/Redo
Core Data comes with an undo manager which tracks changes to it. This undo manager can roll the changes back either individually
or in groups. This makes adding undo/redo support in apps convinient and easy to implement.

NSManagedObjectContext has instance property undoManager of type UndoManager.

### 3. Background data tasks
Potential UI blocking tasks can be performed in background.

### 4. View synchronization
Core Data can also help keeping views updated.

### 5. Versioning and migration
Core Data has provision for versioning data model and also migrating user data.





## Core Data Stack
- Persistent container (NSPersistentContainer)
- Model (NSManagedObjectModel)
- Context (NSManagedObjectContext)
- Store coordinator (NSPersistentStoreCoordinator)


## Good Thing to Know: 
When one want to store images, then one have to set the type to Binary Data and check the Allows External Storage
in the Attribute Inspector. We do this because when we initialize the Core Data, we load all the data to the memory. When 
we have a lot of saved images, we don’t want them to get loaded every time we open the app, but only when it’s time to 
show/use them. This way, we’ll avoid any performance issues.


## Working with Core Data
### Creating a Data Model File (*.xcdatamodeld*)

Select Core Data checkbox while creating a new project in Xcode, or if project is already created then one needs to add
a new file of type Data Model from Core Data section. In both the cases one sees a file with extension *.xcdatamodeld* added
to project.

### Setting up Core Data stack
Core Data stack refers to set of objects which work together in Core Data framework to manage and persist the app’s objects.
Following all form the core data stack

- Persistent container (NSPersistentContainer)
- Model (NSManagedObjectModel)
- Context (NSManagedObjectContext)
- Store coordinator (NSPersistentStoreCoordinator)


## NSPersistentContainer
NSPersistentContainer class represents or encapsulates the Core Data stack in an app. It manages and simplifies the creation
and management of Core Data stack.
Persistent container is defined as a lazy variable (so as to defer instantiation until first use)

So NSPersistentContainer creates:-
- Managed object model (NSManagedObjectModel)
- Persistent store coordinator (NSPersistentStoreCoordinator)
- Managed object context (NSManagedObjectContext)

Example : Refer AppDelegate in below project
https://github.com/saurabh1088/uikit
https://github.com/saurabh1088/uikit/blob/main/UIKitLearnings/UIKitLearnings/AppDelegate.swift


## NSManagedObjectModel
When Core Data is opted for a project either from start or added in between, one ends up with generating a *.xcdatamodeld*
file. NSManagedObjectModel is the programmatic representation of this *.xcdatamodeld* file.

The *.xcdatamodeld* file when opened in Xcode editor allows one to add entities. So basically *.xcdatamodeld* describes the
objects of the object graph Core Data will eventually manage. These entities are represented by NSEntityDescription.

Check file *UIKitLearnings.xcdatamodeld* in project https://github.com/saurabh1088/uikit

So we have a NSManagedObjectModel which is basically *.xcdatamodeld* file, this file contains one or many NSEntityDescription.
NSEntityDescription are the entities which have properties represented by NSPropertyDescription.

An entity's property represented by NSPropertyDescription could be of following types:-
- Attribute (NSAttributeDescription)
- Relationships (NSRelationshipDescription)
- Fetched Properties (NSFetchedPropertyDescription)

NSAttributeDescription, NSRelationshipDescription, and NSFetchedPropertyDescription are all derived from NSPropertyDescription.


## QnA
### When is Core Data initialized?
Core data is initialized on app’s startup.

### Is Core Data a database?
Core Data is NOT a database. It is as mentioned above a framework managing object graph. Data persistence in Core Data is
an optional feature. One can go ahead and use Core Data very well for in-memory data management without ever persisting to
some database.

### Core Data persistence options?
Yes, persistence is optional in Core Data. If one chooses Core Data for data persistence, then one can also specify the type
of persistece store one want to use. Following are options :
- SQLite
- XML
- Binary


## TODOs
- [ ] Check how to specify which persistent store to use and which is default one core data uses.
- [ ] What is Core Data, and what is its primary purpose in iOS development?
- [ ] Explain the role of the Managed Object Model in Core Data.
- [ ] What is a Managed Object Context, and how is it used in Core Data?
- [ ] Describe the purpose of the Persistent Store Coordinator in the Core Data stack.
- [ ] What is a Managed Object, and how does it relate to entities in Core Data?
- [ ] Explain the differences between an entity and an attribute in Core Data.
- [ ] How do you define relationships between entities in the Core Data model?
- [ ] What are fetched properties in Core Data, and when might you use them?
- [ ] What is an NSFetchedResultsController, and how is it used?
- [ ] Compare and contrast NSFetchRequest and NSPredicate in Core Data.
- [ ] How do you perform a fetch request with a sort descriptor in Core Data?
- [ ] Explain the role of the persistent store in Core Data.
- [ ] What types of persistent stores does Core Data support, and how do you choose one for your application?
- [ ] How can you migrate data when you update your Core Data model?
- [ ] What is the typical pattern for managing Core Data contexts in a multithreaded environment?
- [ ] What is a NSManagedObjectContextDidSave notification, and how can it be useful?
- [ ] How can you optimize Core Data fetch requests for better performance?
- [ ] Explain the concept of faulting in Core Data and its impact on performance.
- [ ] How do you handle errors when working with Core Data operations?
- [ ] What is the purpose of the Core Data lightweight migration?
- [ ] How do you implement undo and redo functionality using Core Data's undo manager?
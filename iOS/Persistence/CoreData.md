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


## Is Core Data a database?
Core Data is NOT a database. It is as mentioned above a framework managing object graph. Data persistence in Core Data is
an optional feature. One can go ahead and use Core Data very well for in-memory data management without ever persisting to
some database.


## Core Data persistence options?
Yes, persistence is optional in Core Data. If one chooses Core Data for data persistence, then one can also specify the type
of persistece store one want to use. Following are options :
- SQLite
- XML
- Binary


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
Core data is initialized on app’s startup.
Persistent container is defined as a lazy variable (so as to defer instantiation until first use)


## TODOs
[ ] Check how to specify which persistent store to use and which is default one core data uses.
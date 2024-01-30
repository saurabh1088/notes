# Core Data


## What is Core Data?
Simply stating : *Core Data is a FRAMEWORK*

Core Data is first and foremost a framework for managing an object graph.

Core Data can help to 
- Save application’s permanent data(offline usage)
- Cache temporary data
- To add Undo functionality
- Sync data across multiple devices(using CloudKit working with CoreData)


## What is an Object Graph?
We say Core Data manages object graph, let's see what an object graph is. Objects can and will have references to other
objects in any object oriented programming. These relationships form a graph. One can say that an object graph is conceptualization 
of all instances of the objects from one's object model (the classes in the program) and their interconnections.
So an Object graph is basically a dependency graph between objects.


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

Context needs to know the coordinator to do it's work. Coordinator needs to know about model so that it can make sense of
the persistent stores it manages. So Model, Context and Coordinator are all sufficiently interdependent.
Core Data provided one encapsulated type i.e. NSPersistentContainer which represents this entire stack.


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


## NSManagedObjectContext
Persistent container has a viewContext property of type NSManagedObjectContext, which can be referred as below. NSManagedObjectContext
represents a context which consists of a group of related model objects. These related model objects can represent internally
consistent view of one or more persistent stores. 

```
let managedContext = (UIApplication.shared.delegate as? AppDelegate)?.persistentContainer.viewContext
```

Using this managed context one can access managed objects and have changes apply to those. Changes which are applied to managed
objects will remain in memory until the context is saved to persistent store by Core Data.

Context object has a central role in managing life cycle of managed objects.

### Responsibilities of NSManagedObjectContext
1. Managed objects life cycle management.
2. Undo/Redo
3. Fetch objects from a persistent store
4. Fetch and make changes to objects from persistent store
5. Discard or commit changes to persistent store
6. Watch changes in managed objects
7. Maintains an undo manager
8. Insert new objects or delete existing

## NSPersistentStoreCoordinator
Responsible for managing the persistent stores. Most of the time a persistent store is a database which lives on filesystem.
It's possible to have many persistent stores at once. One can also have custome made one derived from NSPersistentStore.

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


## WWDC

### Making Apps with Core Data
https://developer.apple.com/videos/play/wwdc2019/230/

Cascade deletion rule.
Batch Insertions.
fetchBatchSize : This will set the batch size which gets loaded in memory and not all records from fetch.
NSDiffableDataSourceSnapshot
Denormalization
Derived Attributes : Makes Denormalization super easy
Remote Change Notifications

Core Data objects have supported KVO since beginning, however now once can use Combine to drive changes to UI by subscribing
to publishers on Core Data object properties.


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
- [ ] Watch https://developer.apple.com/videos/play/wwdc2019/220
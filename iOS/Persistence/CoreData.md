# Core Data


## What is Core Data?

Simply stating : *Core Data is a FRAMEWORK*

Core Data is first and foremost a framework for managing an object graph.

Core Data can help to 
- Save application’s permanent data(offline usage)
- Cache temporary data
- To add Undo functionality
- Sync data across multiple devices(using CloudKit working with CoreData)

Core Data abstracts the details of mapping objects to a store, making it easy to save data from Swift and Objective-C
without administering a database directly.

Further more one can define Core Data as :-
A framework used to manage the model layer objects in an application. Core Data provides generalized and automated
solutions to common tasks associated with object life cycle (runtime) and object graph management, including persistence.


## Features of Core Data from bird's eye view

### 1. Persistence
Core Data as mentioned can be used for data persistence by opting for a persistent store. The default store is SQLite.
Core Data provides abstraction over objects mapping to persistent store. This makes easy to save data without having to
administer database directly.

### 2. Undo/Redo
Core Data comes with an undo manager which tracks changes to it. This undo manager can roll the changes back either
individually or in groups. This makes adding undo/redo support in apps convenient and easy to implement.

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


## NSPersistentContainer

- `NSPersistentContainer` class represents or encapsulates the Core Data stack in an app.
- It manages and simplifies the creation and management of Core Data stack.
- Persistent container is defined as a lazy variable (so as to defer instantiation until first use)
- So `NSPersistentContainer` creates:-
    - Managed object model (NSManagedObjectModel)
    - Persistent store coordinator (NSPersistentStoreCoordinator)
    - Managed object context (NSManagedObjectContext)

Example : Refer AppDelegate in below project
https://github.com/saurabh1088/uikit
https://github.com/saurabh1088/uikit/blob/main/UIKitLearnings/UIKitLearnings/AppDelegate.swift


## NSManagedObjectModel

When Core Data is opted for a project either from start or added in between, one ends up with generating a `.xcdatamodeld`
file. `NSManagedObjectModel` is the programmatic representation of this `.xcdatamodeld` file.

The `.xcdatamodeld` file when opened in Xcode editor allows one to add entities. So basically `.xcdatamodeld` describes the
objects of the object graph Core Data will eventually manage. These entities are represented by `NSEntityDescription`.

Check files: 
1. *UIKitLearnings.xcdatamodeld* in project https://github.com/saurabh1088/uikit
2. *LearningAppCoreDataUIKit.xcdatamodeld* in project https://github.com/saurabh1088/ios/tree/main/LearningAppCoreDataUIKit

So we have a `NSManagedObjectModel` which is basically `.xcdatamodeld` file, this file contains one or many `NSEntityDescription`.
`NSEntityDescription` are the entities which have properties represented by `NSPropertyDescription`.

An entity's property represented by `NSPropertyDescription` could be of following types:-
- Attribute (`NSAttributeDescription`)
- Relationships (`NSRelationshipDescription`)
- Fetched Properties (`NSFetchedPropertyDescription`)

`NSAttributeDescription`, `NSRelationshipDescription`, and `NSFetchedPropertyDescription` are all derived from `NSPropertyDescription`.

Once entity is added to `.xcdatamodeld` file, Xcode autogenerates the entity file by naming convention Entity+CoreDataClass.
This generated entity is a public class inheriting from `NSManagedObject`.

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

- Responsible for managing the persistent stores.
- Most of the time a persistent store is a database which lives on filesystem.
- It's possible to have many persistent stores at once.
- One can also have custome made one derived from NSPersistentStore.

- Managed object context uses a coordinator to facilitate the persistence of its entities in the coordinator’s registered
stores.
- Managed object context cannot function without a coordinator because context relies on coordinator's access to managed object
model.
- A persistent store coordinator presents its registered stores as aggregate. This implies that the context can operate on
the union of those stores instead of individually.
- A persistent store coordinator performs its work on a private serial queue.
- One can use multiple coordinators if one requires separate queues.
- Using persistent store coordinator one can
    - Add OR remove persistent stores
    - Change the type of persistent stores
    - Changes the on-disk location of persistent stores
    - Query metadata of specific store
    - Defer store's migration
    - Determine whether two objects originate from the same store
    etc.


## NSFetchRequest

To fetch records from Core Data, one needs to create an instance of NSFetchRequest and then pass it to NSManagedObjectContext
API to fetch results.


## Entity Relationships

Three possibilities in relationships:
1. One to One
2. One to Many
3. Many to Many


## Working with Core Data

### 1. Creating a Data Model File (`.xcdatamodeld`)
Select Core Data checkbox while creating a new project in Xcode, or if project is already created then one needs to add
a new file of type Data Model from Core Data section. In both the cases one sees a file with extension `.xcdatamodeld` added
to project.

### 2. Setting up Core Data stack
Core Data stack refers to set of objects which work together in Core Data framework to manage and persist the app’s objects.
Following all form the core data stack

- Persistent container (NSPersistentContainer)
- Model (NSManagedObjectModel)
- Context (NSManagedObjectContext)
- Store coordinator (NSPersistentStoreCoordinator)


## Core Data and Performance considerations

### 1. Model design : Indexing
Makes sure to design model with indexing in mind so that fetch can be faster.
In Xcode in `.xcdatamodeld` file, for an entity long press on Add Entity button give few options where one of the option is
*Add Fetch Index*. Selecting this options adds a child node to the entity named *byPropertyIndex*, this can be renamed and
configured to provide the index.

### 2. Background managed object context
NSPersistentContainer has instance property *viewContext* which is the managed object context associated with the main queue.
In app using less amount of data in Core Data this won't cause any visible issues. However for large amount of data slow queries will start blocking the main queue and cause UI responsiveness issues.
Ideally data processing should be on background queue. One can opt for a different managed object context operating on a
background queue. NSPersistentContainer has instance method *newBackgroundContext()* for this purpose which creates and
returns a new *NSManagedObjectContext* associated with a private queue.

### 3. Fetch : Use predicates to restrict number of fetched records
While fetching records from core data, fetch only the records required using predicates. If data set is huge then loading
all data without need will consume resources unnecessarily.

### 4. Batch updates

### 5. Faulting


## UndoManager

UndoManager is not specific to Core Data Framework. It is a general purpose class which records operations performed and
enables functionallity of undo and redo.
*NSManagedObjectContext* has an instance propery *undoManager* on type *UndoManager* providing support for undo/redo operations
for the context.

The default value of NSManagedObjectContext's undoManager is nil, so before using, one needs to set it.

*UIResponder* also has an instance property *undoManager*. Every window of an app has a undo manager, which is a shared
object for managing undo and redo operations. Also in the responder chain any object part of responder chain can have their
own custom undo manager.

Example : Refer AppDelegate in below project
https://github.com/saurabh1088/ios/tree/main/LearningAppCoreDataUIKit
https://github.com/saurabh1088/ios/blob/main/LearningAppCoreDataUIKit/LearningAppCoreDataUIKit/Movies/MoviesViewModel.swift


## Handling Conflicts

### What are conflicts?
Conflicts can arise in core data when simultaneously attempt is made to modify same data. This can happen in app multiple
part attempting to modify same data or due to concurrency.

### How to resolve the conflicts?
1. Core Data built-in merge policies refer below for more details
https://developer.apple.com/documentation/coredata/nsmergepolicy/merge_policies


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
- XML (Not available on iOS)
- Binary


## How to specify which persistent store to use and which is default one core data uses?

Core data default persistent store is SQLite. There are options to use XML, Binary o r in-memory as well. To specify a store
other than the default one, one need to create `NSPersistentStoreDescription` and assign it's `type` property to available
options like
- `NSInMemoryStoreType`
- `NSSQLiteStoreType`
- `NSBinaryStoreType`
For example :
https://github.com/saurabh1088/ios/blob/main/LearningAppCoreDataInMemoryUIKit/LearningAppCoreDataInMemoryUIKit/CoreDataManager.swift


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


## Core Data Migration

### WWDC 2022
Evolve your Core Data schema
https://developer.apple.com/videos/play/wwdc2022/10120/


### What is schema migration and why is it required?
For an application using Core Data, it is a certainty that at some point the data models will need to be updated based on growing or changing business functionalities. Any updates to the data models will necessitate that the underlying persistent storage is also updated. Without updating schema to reflect changes in model will lead to issues like Core Data refusing to open the persistent store.

### What is the error Core Data gives if the model mismatches with the underlying scheme?
If one tries to open an incompatible store, which means, the model is updated but the underlying scheme is not migrated yet, then one receives error code NSPersistentStore- IncompatibleVersionHashError. Receiving this error is most likely indication of that data migration is required.

### How to perform Data Migration in Core Data?
Core Data provides built-in data migration tools which enables one to keep the app's data storage up-to-date with the current data model.
These tools are referred to as `Lightweight Migration`

### Lightweight Migration
Lightweight migration automatically analyzes and infers the migration from the differences between the source and destination managed object models.

### Lightweight Migration and changes to Attributes Support
- Adding an attribute
- Removing an attribute
- Making a non-optional attribute optional
- Making an optional attribute non-optional and defining a default value
- Renaming an attribute

### Lightweight Migration and changes to relationship support
- Add
- Delete
- Change relationship cardinality (one-to-one TO one-to-many)


### Lightweight migration is controlled by two options keys
- NSMigratePersistentStoresAutomaticallyOption
- NSInferMappingModelAutomaticallyOption.


## TODO: Move this to proper location
## About Transient

Properties—relationships as well as attributes—may be transient. A managed object context knows about transient properties
and tracks changes made to them. Transient properties are ignored by the persistent store, and not just during saves:
one cannot fetch using a predicate based on transients (although one can use transient properties to filter in
memory).


## TODO: Move this to proper location
## NSManagedObjectContext Parent Child scenario

- It has a property `var parent: NSManagedObjectContext?`
- This property can point to a parent context
- This can create a chain of parent child relationship which eventually will culminate in a NSManagedObjectContext having parent as nil.


## Good Thing to Know:

When one want to store images, then one have to set the type to Binary Data and check the Allows External Storage
in the Attribute Inspector. We do this because when we initialize the Core Data, we load all the data to the memory. When 
we have a lot of saved images, we don’t want them to get loaded every time we open the app, but only when it’s time to 
show/use them. This way, we’ll avoid any performance issues.


## Can a core data stack have more than one managed object model, the `.xcdatamodeld` file?

YES, this is possible by merging all the `NSManagedObjectModel` together into one single model using instance method
`mergedModel(from:)`.

## Explain the concept of faulting in Core Data and its impact on performance.

Core Data is a framework which is highly performant. Core Data works on records from persistent stores once those are loaded
into memory. Which is to say that there is no direct actions on the persistent store. This means object need to be loaded
into memory, but this can cause issues if everything is loaded into memory. So Core Data employs technique of faulting to
optimise the memory usage. The way faulting works is that Core Data only fetches data which is absolutely needed to satisfy
requirement of application.

Faulting basically defers loading of actual data until it is needed. What Core Data does is that it in order to manage memory
usage efficiently, loads lightweight fault placeholders objects instead of fully realised managed objects. When the property
which at present is a fault is actually accessed then Core Data with fire the fault and fetch data from persistent store
to fully realise it. This is kind of a lazy loading which reduces memory footprint and imporoves performance when dealing
with very large datasets.

When objects are fetched in Core Data, usually those start as faults. Faults one can say are lightweight proxies for the
actual objects. For example while loading say 1000 records of some object model Employee, Core Data will create 1000 fault
objects for Employee without loading all attributes, relationships until one uses those.

So one can see the impact of performance as that while running faulting leads to : 
- lesser memory footprint for the app
- faster initial load time


## What is an Object Graph?

We say Core Data manages object graph, let's see what an object graph is. Objects can and will have references to other
objects in any object oriented programming. These relationships form a graph. One can say that an object graph is
conceptualization of all instances of the objects from one's object model (the classes in the program) and their
interconnections.
So an Object graph is basically a dependency graph between objects.


## TODOs

- [x] Check how to specify which persistent store to use and which is default one core data uses.
- [x] What is Core Data, and what is its primary purpose in iOS development?
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
- [x] Explain the concept of faulting in Core Data and its impact on performance.
- [ ] How do you handle errors when working with Core Data operations?
- [ ] What is the purpose of the Core Data lightweight migration?
- [ ] How do you implement undo and redo functionality using Core Data's undo manager?
- [ ] Watch https://developer.apple.com/videos/play/wwdc2019/220
- [ ] Check https://www.avanderlee.com/swift/core-data-performance/
- [ ] Can a persistent container have multiple managed object model. Case in point NSPersistentContainer has a property managedObjectModel. Explore this.
- [ ] How to define a transient entity?
- [ ] What is the role of NSManagedObjectID?

Core Concepts
- [ ] What is Core Data? How does it differ from SQLite?
- [ ] Core Data Stack: Explain the components of the Core Data stack (NSManagedObjectModel, NSPersistentStoreCoordinator, NSManagedObjectContext).
- [ ] Core Data Relationships: Describe the different types of relationships in Core Data (one-to-one, one-to-many, many-to-many). How do you model them?
- [ ] Faulting and Fetching: Explain the concept of faulting and fetching in Core Data. How can you optimize fetching performance?
- [ ] Concurrency: How do you handle concurrency in Core Data? What are the best practices for managing multiple contexts?

Advanced Topics
- [ ] Performance Optimization: What techniques can be used to optimize Core Data performance, especially for large datasets?
- [ ] Migration: How do you migrate Core Data models when the app's data model changes?
- [ ] Data Validation: How do you validate data in Core Data to ensure data integrity?
- [ ] Background Tasks: How do you perform background tasks with Core Data, such as background fetching and saving?
- [ ] Security: How do you protect sensitive data stored in Core Data?

Practical Scenarios
- [ ] Large Datasets: How would you handle a large dataset in Core Data? What strategies would you use to optimize performance and user experience?
- [ ] Complex Data Models: How would you model a complex data model with many relationships and constraints in Core Data?
- [ ] Offline First: How would you implement an offline-first strategy with Core Data?
- [ ] Real-time Updates: How would you synchronize Core Data with a remote server in real-time?
- [ ] Testing Core Data: How do you test Core Data-backed apps, especially unit testing and UI testing?


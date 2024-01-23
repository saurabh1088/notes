# Core Data


## What is Core Data?

Simply stating : *Core Data is a FRAMEWORK*

Core Data is first and foremost a framework for managing an object graph.

It can help to 
- Save application’s permanent data(offline usage)
- Cache temporary data
- To add Undo functionality
- Sync data across multiple devices(using CloudKit working with CoreData)


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


## NSPersistentContainer
Core data is initialized on app’s startup.
Persistent container is defined as a lazy variable (so as to defer instantiation until first use)


## Good Thing to Know: 
When one want to store images, then one have to set the type to Binary Data and check the Allows External Storage
in the Attribute Inspector. We do this because when we initialize the Core Data, we load all the data to the memory. When 
we have a lot of saved images, we don’t want them to get loaded every time we open the app, but only when it’s time to 
show/use them. This way, we’ll avoid any performance issues.


## TODOs

1. Check how to specify which persistent store to use and which is default one core data uses.
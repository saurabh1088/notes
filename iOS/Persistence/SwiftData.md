# Swift Data

## What is SwiftData?

_SwiftData is a powerful framework for data modelling and management which enhances the modern Swift app._

Like SwiftUI, SwiftData focuses entirely on code with no external file formats and uses Swift's new macro system to
create a seamless API experience.
SwiftData relies on the expressivity provided by the new Swift language macros in order to create a seamless API experience.
And it is naturally integrated with SwiftUI and works with other platform features, like CloudKit and Widgets.


## @Model Macro
- Helps to define application's schema with Swift code
- Adds SwiftData functionality to model types
- SwiftData natively adapts value type properties to be used as attributes right away.
- @Model will modify all the stored properties on type.


Models in SwiftData are the source of truth for an application's schema and drive the persistence experience.
SwiftData schemas are normal Swift code, but when needed, one can annotate properties with additional metadata.
SwiftData models reference types as relationships.
One can influence how SwiftData builds one’s schema using metadata on the properties. For example :
- @Attribute : add uniqueness constraint
- @Relationship : choice of inverses and specify delete propagation rules
- @Transient : Not to include the property for persistence

## ModelContainer & ModelContext
- The model container provides the persistent backend for model types
- One can use default settings for ModelContainer or customise it with configurations and migration options
- One can create a model container just by specifying the list of model types one want stored
- Once container is set-up, one can fetch and save data with model contexts
- Model contexts observe all the changes to app's models and provide many of the actions to operate on them
- In SwiftUI, one will generally get the modelContext from the view's environment after one creates the model container.
- To use SwiftData, any application has to set up at least one ModelContainer.
- A View has a single model container, but an application can create and use as many containers as it needs for different view hierarchies.
- Many applications need a single model container. In this case, one can set it up for the whole window group scene. The window and its views will inherit the container, as well as any other windows created from the same group. All of these views will write and read from a single container.
- To access the model context, SwiftUI offers a new environment variable.
- One might think that after inserting the model, one need to save the context, calling `modelContext.save(),` but one doesn't need to do that. A nice detail about SwiftData is that it autosaves the model context. The autosaves are triggered by UI-related events and user input. We don’t need to worry about saving because SwiftData does it for us. Though save can be called explicitly as well if required as per use case.


## @Query
- Provides view with data
- Triggers view update on every change of models
- A view can have multiple @Query properties
- Use @Query whenever one want to display models, managed by SwiftData, in the UI
- @Query is a new property wrapper that queries the models from SwiftData.
- Query offers lightweight syntax to configure 
    - sorting
    - ordering
    - filtering, and 
    - even animating changes.
- Under the hood, it uses a model context of the view as the data source.
- How do we provide @Query with a model context? We'll get one from a model container


## What is a document based app in Apple’s ecosystem?
Document-based apps is a concept used on macOS, iOS, and iPadOS. It describes the certain types of applications that allow users to create, open, view, or edit different types of documents. Every document is a file, and users can store, copy, and share them.



## Schema Macros
- @Attribute schema macro and using the unique option - For unique constraints
- @Attribute with originalName : Map property name to original name without data loss
- If one doesn’t wants to persist some properties in model then use @Transient macro


## Migrate to SwiftData

### How can one generate SwiftData Model Classes using the Managed Object Model Editor assistant?
From an existing Core Data model, it is possible to generate SwiftData model classes. Generated classes also follow the organization already in the preexisting model.
To do this, one need to go through project’s Managed Object Model Editor assistant. Select the model file and then from meny bar one need to, select Editor, and click on Create SwiftData Code.
This will generate required classes.


### Can SwiftData and CoreData co-exist in an application?
YES. It might be not possible to fully migrate an application from using CoreData to fully using SwiftData. In such cases one can opt for a partial conversion to SwiftData. What co-existence of CoreData and SwiftData would mean is that there are two completely separate persistent stacks, one Core Data stack and one SwiftData stack, talking to the same persistent store. What this implies is that one need not to completely rewrite existing Core Data code in order to be able to start adding SwiftData code.
Before loading the persistent store, one need to set the persistent store URL for the container description to ensure that both stacks(CoreData and SwiftData) are writing to the same URL. Additionally, one also need to turn on persistent history tracking. While SwiftData automatically turns on persistent history tracking, Core Data does not.
If application having both Core Data and SwiftData coexisting, tries to open a persistent store without setting the persistent history, the store will be put into read-only mode.
Some important points to make sure when working with CoreData and SwiftData both in same application.
- One should use namespace for preexisting NSManagedObject based entities or SwiftData classes so that they should not collide.
- CoreData and SwiftData schemas need to be in sync.



### Full migration from CoreData to SwiftData.
When one is migrating an application from CoreData to SwiftData, then one is replacing the CoreData stack with SwiftData stack. Before this migration one need to consider how the preexisting core data model designs are structured. An application’s Core Data model designs refer to the schema, including the entities and their properties and relationships.
One need to make sure that the Core Data model designs are supported in SwiftData as well. This means that for each entity that was defined in Core Data, there needs to be a corresponding model type with exact matches for entity name and properties in SwiftData.



## Sources
WWDC 2023
Meet SwiftData
https://developer.apple.com/videos/play/wwdc2023/10187/

WWDC 2023
Build an app with SwiftData
https://developer.apple.com/videos/play/wwdc2023/10154

WWDC 2023
Model your schema with SwiftData
https://developer.apple.com/videos/play/wwdc2023/10195

WWDC 2023
Migrate to SwiftData
https://developer.apple.com/videos/play/wwdc2023/10189/

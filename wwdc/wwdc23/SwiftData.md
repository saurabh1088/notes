#  SwiftData

## SwiftData is a framework

It’s for :
- Data modelling and management
- enhances modern Swift app
- focuses entirely on code with no external file formats
- Uses Swift’s new macro system
- Naturally integrated with SwiftUI
- Available across all the platforms

## @Macro
Model macro

- New Swift macro
- Using Model macro makes a class fully persistable with SwiftData
- Defines schema with code
- Adds SwiftData functionality to model types
- Models in SwiftData are source of truth of app’s schema and drive the persistence experience
- When model macro is used, attributes are inferred from properties right away (basic types are supported as well as struct, enum, codable, collection of value types etc)
- Relationships are inferred from reference types
- Modifies all stored properties
- One can influence how properties are inferred using @Attribute and @Relationship metadata
- One can tell SwiftData not to include specific properties using @Transient

## Model container

- Provides persistence backend for model types
- Can be customised with configurations and migration options
- Can be created with list of model types one want to be stored
- Once container is set up, one is ready to fetch and save data using model context
- SwiftUI has new modifiers to set up context and containers for view’s environment

## Model Context

- Model contexts observe all the changes to models
- Interface to 
    - Tracking updates
    - Fetching models
    - Saving changes
    - Undoing changes

## Fetching data

- New Swift native types
    - Predicate (Replacement for NSPredicate)
    - FetchDescriptor


## SwiftData & SwiftUI

- Seemless integration
- Automatically fetch data and update views

## @Query

- New property wrapper
- To use data managed by SwiftData in a view one needs to use this property wrapper
- Triggers view update whenever model changes
- Views can have multiple @Query annotated properties
- @Query is using ModelContext behind the scenes as source of data


## Building app with SwiftData

- One needs to use @Model macro on the models which would have initially conformed
ObservableObject protocol with @Published annotated properties.

- Conformance to ObservableObject is not required.

- @Published property wrapper is also not required.

- View's using any ObservableObject needed to annotate property with @ObservedObject.
This need to be replaced with @Bindable property wrapper.

- To use data managed by SwiftData in a view one needs to use property wrapper
@Query

- @Query is a new property wrapper.

- To use SwiftData, any application need to set up at least one ModelContainer

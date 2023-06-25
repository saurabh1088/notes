#  SwiftData

## SwiftData is a framework

It’s for :
- Data modelling and management
- enhances modern Swift app
- focuses entirely on code with no external file formats
- Uses Swift’s new macro system
- Naturally integrated with SwiftUI

## @Macro
Model macro

- New Swift macro
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

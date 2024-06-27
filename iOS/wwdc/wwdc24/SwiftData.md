#  SwiftData

## Source
What’s new in SwiftData
https://developer.apple.com/videos/play/wwdc2024/10137/


## Unique : ✨NEW THIS YEAR
- It's a new schema macro introduced this year
- This macro allows one to construct compound constraint on persistent models.
- This macro tells SwiftData that which all properties in model need to remain unique.
- If an attempt is made to insert a model with a property which is expected to be unique, and if a record already exists
in persisted data with same unique value, then SwiftData will be smart enough to do an upsert(upsert is update if exists, 
else insert) here
- Unique makes it easy to avoid data duplication while doing persistence using SwiftData

## Reveal history with SwiftData
- SwiftData history provides a way for app to know what models were inserted, updated or deleted over time.
- When models are deleted, values marked to be preserved(one can do so using Attributes macro) are kept in the history information as tombstone values, giving the app the information it may need to process those changes.
- History work with custom data stores as well
- [ ] TODO: Watch more on this - [Track model changes with SwiftData history](https://developer.apple.com/videos/play/wwdc2024/10075)


## Tailor a container
- Tailoring a model container allows an app to fine tune its data location and how it is used throughout the app.
- Fully customisable data stores
- Custom Data Stores
    - Custom data stores let’s one use familiar SwiftData APIs
- [ ] TODO: Watch more on this - [Create a custom data store with SwiftData](https://developer.apple.com/videos/play/wwdc2024/10138)


## Preview Data using traits
- PreviewModifier : ✨NEW THIS YEAR
- @Previewable macro : ✨NEW THIS YEAR
    - this can be used along with @Query macro


Optimize Queries
Create compound predicates

Expression macro ✨NEW THIS YEAR to build complex predicates

- Index macro ✨NEW THIS YEAR which provides ability to create single or compond index on some model
- Index represents additional metadata which SwiftData generates and saves in the container
- This added metadata makes queries for specified keypaths faster and more efficient
- To get this metadata one needs to specify which properties SwiftData should create an index for. Consider properties most frequently occuring in sorting and filtering queries.

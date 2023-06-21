#  String Catalogs

_ A localizable string is a string which will be shown on user interface at runtime
hence need to be translated to user's selected language considering all languages
app supports_

Traditionally localizations are handled in an app via Localizable.string files for
each supported language containing key value pairs and then in another dictionary
keeping key reference to further use in code.

TODO: Check stringsdict file

String Catalogs introduced with Xcode 15 aims to make this process easy.

Xcode 15 introduces Strings Catalog which will replace the existing process of 
keeping both strings and stringsdict files in Xcode. It will keep all strings to be 
localized in one place and will help make sure app is shipped with all content
localized.

- Xcode automatically extracts string from code and keeps them in string catalog
file, so one doesn't need to add strings by themselves.

- String catalog will also update if the string used in code is using any arguments.

- For multiplatform apps, it is possible to add flavor for a platform which help
to use specific string for specific platform.

## Extract

Xcode can extract localizable strings from :
- Swift/Objective C code
- SwiftUI Views
- Storyboards & xibs
- C code
- Info plist

Localizable.xcstrings(the string catalog) if exists, Xcode will pull localizable 
strings from these sources and update the file.

LocalizedStringResource is the recommended type for representing and passing around
localizable strings. This is because it supports initialization using string literal
and can also be provided with a comment, table name and a default value.

Custom MACROS in Objective C taking string can also be configured via build settings
to get extracted.

NOTE: One needs to enable in Build Settings _Use Compiler to Extract Swift Strings_

Xcode will make best efforts to keep string catalog up to date

Everytime project is build, Xcode will extract and update string catalogs.

If for a localized string there is no localizations added yet, then if this string
is removed from code/storyboard etc then Xcode will update and delete it from
string catalog as well.
If however the localized string did had translation present, then when deleted from
source, Xcode will mark the entry in string catalog as STALE.
One can also mark a string to be manually managed so as to avoid Xcode updating or
deleting it after build.


## Edit

String catalog provides first class support for showing the state of localized string
and the progress of translations achieved.

State badges
- STALE : Not found in code
- NEW : Not translated
- NEEDS REVIEW : May need some change
- Green Checkmark : Translated

String pluralization with String Catalog
- String catalog has built in support for string variation workflows requiring string
pluralization. Context menu on a string in string catalog can help add a variation
to it by plural.
- Complext plural strings (where more than one word can be plural with various combinations),
string catalog provide built in support to add substitution for each of those words
prefixed with @ sign.


## Export

Xcode offers export localizations generating industry standard .xliff files

## Build

Under the hood, the string catalog files are JSON, so they are easily diffable in
version control systems.
At build time, string catalog files are compiled to .strings and .stringsdict files.

NOTE: Strings catalog are back-deployable, so can be used for any OS.

## Migrate

Right click on existing localizable file and choose migrate to string catalog

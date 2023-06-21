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
- Code
- Interface builder files
- Plists


## Edit


## Export


## Build

## Migrate

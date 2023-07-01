#  Xcode 15

- All simulators are now downloadable.
- Xcode now when downloaded, the size is smaller, by default all platforms are not
downloaded, while installation one can choose what all to opt for.


## Editing

### Code completion

- While creating a struct or class, autocompletion will now suggest name as per filename

- The way some auto-completion are presented are improved too. Now one can see all
possible combinations of default arguments to help pick one. (Press right arrow on 
keyboard to reveal all possibilities)

- Completions have more context awareness, thereby giving much better suggestions.

- Suggestions now also consider surrounding code.

### Assets name

- Name provided to assets now can directly be used within code without any need to
declare those as strings and creating for eg any enum. Code completion will also
suggest asset names when used.

### String catalog

- Refer https://github.com/saurabh1088/notes/blob/main/wwdc/wwdc23/StringCatalogs.md


## Documentation

- Assistant showing real-time preview of documentation
- Editor -> Assistant ->


## Quick Actions

- Command + Shift + A


## Swift Macros

- Xcode gives capability to allow using macro generated code like any other code in app
- Macros are part of Swift packages in the SDK
- Use quick actions in Xcode to expand and view macro code
- One can even set-up a breakpoint in macro for debugging


## Previews

- Previews now take advantage of macros. #Preview macro help generate previews
- Previews are now also available for UIKit and AppKit
- Also introduces to build widgets


## Navigation

- Bookmark navigator : It's present right next to source control navigator in left navigation bar
- One can right click and select add bookmark in context menu to create a bookmark
- Added bookmark shows up in the navigation menu, it's description can be changed
- Xcode annotates and highlights the line where bookmark was added
- Bookmarks can be sorted and grouped together
- Bookmarks can be used as a TODO list as well and can be marked as completed
- Bookmarks can't just be used on line of codes, but queries can also be bookmarked


## Sharing

### Source control navigator

- Improved reporting and staus for each files having changes
- Clicking on Uncommited changes brings up the Commit Editor
- All modifications can be review in a single scrolling view
- Some context is shown by default, if needed one can drag and see additional context
- Files can be edited right therein the Commit Editor itself, new changes is shown as unstaged
- Staging and unstaging can be done right there in Commit Editor itself


## Testing

- Updates test navigator, re-written from ground up to be more efficient
- One can search tests based on any result type, such as expected failure
- Test reports are more detailed

### NEW Automation explorer

- It is interactive, so one can watch test playback or can scrub through timeline. 
- Touch and mouse events are overlayed in video.
- At point of failure one can inspect view hierarchy

TODO: Watch : Fix failures faster with Xcode test reports


## Debugging


- OSLog integration in Xcode
- OSLog keeps log output organized
- Xcode 15 console introduces full support for OSLog
- Complex filtering on log data is also available in Xcode console
- Background color of each log entry is based on severity
- Metadata fields are hidden by default, but always just a couple of clicks away
- One can jump from a log entry in Xcode console, directly to the line of code which created it.

### Xcode Debug Console

### New in debug console

- Console no longer pre-fixes metadata before each log line

- Metadata can still be opted to be shown with option to select what information 
one wants to see

- Metadata now comes below each log line, with smaller font and is more subtle 
so focus isn’t drawn away from intended output

- Logs also come with some background appropriately representing error or fault etc

- A pop up window can also show when a log line is selected showing it’s related 
metadata, if one doesn’t wants to see metadata for all the log lines at once, this 
also displays the name of the function which emitted the log line.

- Console has some new tricks for filtering, it can perform complex, tokenized 
filtering. Also console has options to create filters.

- Filter box in console bottom right corner now gives suggestions in a pop-over 
window as well as some pre-defined filters which can be applied.

- Right clicking a log line in Xcode console also gives a context menu from where 
one can hide or show similar logs

- Hovering over a log line in console also enables a source code locator which 
can be used to jump to the code producing the log line


### LLDB

- po will simply print address of a type if the type doesn’t conforms to CustomStringConvertible, 
so p can be used. Similarly there are various other options which one can use from 
LLDB which could be overwhelming to remember. So NEW dwim-print is introduced where 
dwim stands for do-what-i-mean. dwim allows to use a single command to evaluate 
many different expressions in code

- Previous p alias is replaced to perform dwip-print command

- Previous po alias is also replaced to perform dwip-print + object description 


### Tips for logging

- print should rarely be used for logging, it’s far better to use OSLog to obtain 
structured logging

- Always create multiple log handles as per different componenets, this allows 
to set meaningful search terms

- Use OSLogStore to collect valuable diagnostics

- OSLog is a tracing facility capable of providing complex performance analysis 
using instruments tracing


## Distribution


- Easier and safer
- Xcode cloud supports to add test notes, right along side source code, these get 
automatically attached to TestFlight build for distribution and will appear to testers
right alongside the app.
- Xcode cloud now supports notarization of Mac apps.
- Signature verifications for XCFrameworks, authors can digitally sign their xcframeworks
and now one can verify these signatures right in Xcode
- XCFramework authors can now implement a privacy manifest in their framework. This manifest
tell exactly how app uses and protects sensitive data.
- TestFlight internal testing distribution option.



#  QnA SwiftUI

## 1. When and where to call an API in SwiftUI when a view appears?

One should use *task(priority:_:)* or *task(id:priority:_:)* for calling any asynchronous operations when view appears.
The advantage of using these is that if the view dissapears or is removed by SwiftUI then SwiftUI will cancel the task
automatically.

*task(priority:_:)* or *task(id:priority:_:)* are recommended ways for performing asynchronous operations and preferred
over *onAppear(perform:)*


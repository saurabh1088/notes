#  VIPER

VIPER is an architectural pattern one can use and follow in application code.
VIPER pattern helps in separation of code by adopting single responsibility principles
in various layers which it stands for.

In separating the layers of application code into different responsibilities as per
layers defined by VIPER architecture, one advantage is also that the code becomes
more testable from unit test perspective.

## View
## Interactor
## Presenter
## Entity
## Router


## View

Self explanatory, view layer as in most design patterns will take the responsibility
to take user actions and pass to next layer. Next layer when talking in terms of 
VIPER architecture will be Presenter.

## Interactor

Interactor has the Business Logic. Interactor usually represent a single business
use case within an app serving various business functionalities. Interactor should
be designed and written in a way so that it should be independent of the View layer.

## Presenter

Presenter sits between View, Interactor and Router and mediates flow amond these.
On a user action on View layer if required, Presenter can ask for data from Interactor.
Once it gets data it will send to View, also if required it can ask Router for 
navigation.

## Entity

It's just a simple model. In case application is using Core Data then the managed
objects should remain behind the data layer, which means one should still define
Entities and let Interactor work with Entity rather than working directly with
NSManagedObjects.

## Router

Router is kind of a wireframe which has all the navigation logic, it tells which
screen need to be shown and when.


View KNOWS Presenter
Presenter KNOWS Router & Interactor
Interactor CONNECTS TO Networking/Core Data etc services


## https://www.objc.io/issues/13-architecture/viper/

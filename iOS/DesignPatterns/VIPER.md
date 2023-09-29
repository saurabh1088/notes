#  VIPER

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

Interactor has the Business Logic.

## Presenter

Presenter sits between View, Interactor and Router and mediates flow amond these.
On a user action on View layer if required, Presenter can ask for data from Interactor.
Once it gets data it will send to View, also if required it can ask Router for 
navigation.

## Entity

It's just a simple model.

## Router

Router is kind of a wireframe which has all the navigation logic, it tells which
screen need to be shown and when.

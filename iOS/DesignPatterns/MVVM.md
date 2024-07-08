#  MVVM

## What is MVVM?
MVVM is Model View ViewModel. It aims to separate application's business and presentation logic from UI layer.

## Benefits?

### 1. Separation of Concerns
MVVM aims to have a clear distinction between view layer and application's business and presentation logic.

### 2. Code Modularity
Separation of concerns lead to clear distinction in codebase regarding functionalities, resulting in a modular codebase.

### 3. Testability
With UI layer free from business logic, code becomes more testable as one can easilty test business logic by writing unit
tests without need for UI.

### 4. Code Re-usability
One can re-use viewmodels in the application for similar functionalities which promotes code re-usability.


## Where should business logic go, in Model or ViewModel?

### 1. Case study One
Let's assume one needs to build a solution for some company to manage employee database with a simple use case to add new
employees, update existing ones or delete. Now here we will have some model representing employee. Suppose initially it
was required to create a front end app which provides interface to add, update and delete employee details.
So now, for this application one can go ahead and put the business logic into view-model layer. So we can have a view-model
with below functionalities :-

EmployeeViewModel
    - addEmployeeWith(details: Details)
    - updateEmployee(details: Details)
    - deleteEmployee(details: Details)

These could be called from view layer like below

EmployeeView
    - addEvent()
        - viewModel.addEmployeeWith(details: Details)
    - updateEvent()
        - viewModel.updateEmployee(details: Details)
    - deleteEvent()
        - viewModel.deleteEmployee(details: Details)

This will work fine. But. Now suppose we want to add another interface which say just update some details for all the
employees in a go. Let call this new interface as BatchUpdatesView. Now one can create a new viewModel and add required
functionalities. Or in order to use the existing log for adding, deleting, updating single employee, one can use existing
EmployeeViewModel with added batch update functionalities. Adding a new viewmodel will result in duplication. Adding inside
existing viewmodel will eventually make it fat.

A better solution could be if the business logic of adding, deleting and updating could be part of model itself.


## For an app using MVVM design pattern, what happens to viewcontrollers. What role they play?
Even with a UIKit app using MVVM design pattern, one still has to deal with viewcontrollers. Whole problem with MVC design
patters with respect to iOS apps was viewcontrollers becoming too fat and having too much responsibilities. MVVM design
tries to offload some responsibilities from viewcontrollers. Hence viewcontrollers become light weight but they still have
key responsibilities to take care.
- Viewcontroller will still play a role in responder chain.
- Viewcontroller will manage the view hierarchy.
- Viewvontroller is the place which sets up the data bindings with the viewmodels.
- Viewcontroller take responsibility for navigation using segues or navigation controllers.

## TODOs
- [x] For an app using MVVM design pattern, what role would viewcontroller perform?
- [ ] How does information comes to view model in MVVM design pattern?
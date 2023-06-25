#  Unit Testing

## Benefits of writing unit tests.

One might think why to write unit tests after all. Many projects being run with 
little emphasis given to writing unit tests. But writing unit tests has actually 
lots of benefits.

1. Obvious benefit for writing anything to test is that it will eventually test 
the code and help in finding issues(provided tests themselves are written smartly)

2. One can’t just write code and then just write unit tests mutually exclusively. 
The code itself needs to be written in a way to make it unit testable(think dependency 
injection for eg). This forces developers to structure and write code in much better way.

3. One can find issues with code like for eg code repetition while writing unit tests.


## Arrange-Act-Assert

Unit tests should be approcahed following Arrange-Act-Assert methodology
- Arrange : Setting up necessary pre-conditions
- Act : Perform action/method one wants to test
- Assert : Verify


Can we unite test private members?

NO, private members are not accessible. Internal are accessible once target under 
test is annotated as @testable. But private remain not accessible. Also the private 
members must be called from somewhere in the application so those must have already 
been tested or appropriate public/internal apis should be tested to make call to 
private ones.

## Retrospective Test-Driven Development (Retrospective TDD)

Retrospective Test-Driven Development is a development approach combining elements 
of Test-Driven Development (TDD) with the retrospective practice of reflecting on 
past work and making improvements.

In traditional TDD, tests are written before the implementation code, guiding the 
development process. Retrospective TDD, on the other hand, involves writing tests 
after the implementation code has been written. The retrospective aspect comes into 
play during the development cycle, where the focus is on looking back at the code 
that has been written and adding tests to cover the existing functionality.

The main goal of retrospective TDD is to improve the quality and maintainability 
of existing code by adding tests. By writing tests retrospectively, developers 
can identify areas of the codebase that lack proper test coverage or have potential 
issues. It allows developers to take a step back, evaluate the code they have written, 
and ensure that it is adequately tested.

In a retrospective TDD normally below steps are followed :

1. Identify Code Areas: 
Review the existing codebase and identify areas that need better test coverage 
or areas that have a higher likelihood of containing bugs or issues.

2. Write Tests: 
Based on the identified areas, write tests that cover the desired functionality 
or address the potential issues. These tests should verify the expected behavior 
and ensure that the existing code works as intended.

3. Refactor and Improve: 
While writing tests, you may come across code sections that can be improved or 
refactored to enhance readability, maintainability, or performance. Take this 
opportunity to make the necessary improvements.

4. Run Tests: 
Execute the newly written tests along with the existing test suite to verify the 
correctness of the code and ensure that the changes introduced by the tests do not 
break any existing functionality.

5. Iterate: 
Repeat the process periodically or as needed. As you make changes or add new features 
to the codebase, revisit the retrospective TDD approach to ensure that the code 
remains well-tested and maintainable.

6. Retrospective TDD can be a valuable practice to improve the quality of legacy codebases 
or projects that were initially developed without a strong emphasis on automated testing. 
It allows developers to incrementally add tests to existing code, reducing the 
risk of introducing regressions or breaking existing functionality while increasing 
confidence in the codebase.

## XCTest

XCTest is a framework which enables one to create and run :-
- Unit tests
- Performance tests
- UI tests

### Test cases
One adds test cases, test methods and test target for project.
Tests are added by writing one or more test methods which verifies some logic written
in for the app. Then related test methods are grouped in a test case. This test case
is a subclass of XCTestCase.

So a test case is a group of test methods and optionally it may also contain setup
and teardown methods before and after test run.

_For eg. In a typical MVVM design pattern, one has business logic residing in the
view model layer. One writes unit tests for the view model layer, thus one can write
a XCTestCase derived test case class for each view model and then write test methods
covering funtionalities._

### Test method
A test method is an instance method defined in test cases classes, which are subclassed
from XCTestCase. These SHOULD begin with "test" and takes no parameter and return
no value. 
It's a good practice to have meaningfull names which makes the intent of test method
and test case class clear of what is being tested. This is so because test case and
test method names are further used in test execution reports so it's easier to analyse
what is failing.

### Set Up & Tear Down
Tests need to start from a known, predictable state. There can be scenarios where
one needs to:- 
1. Set state once for all test methods in test case
2. Set/reset state for each test method execution
3. Release/delete resource once test method completes
4. Release/delete resource once test case completes

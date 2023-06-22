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

Identify Code Areas: 
Review the existing codebase and identify areas that need better test coverage 
or areas that have a higher likelihood of containing bugs or issues.

Write Tests: 
Based on the identified areas, write tests that cover the desired functionality 
or address the potential issues. These tests should verify the expected behavior 
and ensure that the existing code works as intended.

Refactor and Improve: 
While writing tests, you may come across code sections that can be improved or 
refactored to enhance readability, maintainability, or performance. Take this 
opportunity to make the necessary improvements.

Run Tests: 
Execute the newly written tests along with the existing test suite to verify the 
correctness of the code and ensure that the changes introduced by the tests do not 
break any existing functionality.

Iterate: 
Repeat the process periodically or as needed. As you make changes or add new features 
to the codebase, revisit the retrospective TDD approach to ensure that the code 
remains well-tested and maintainable.

Retrospective TDD can be a valuable practice to improve the quality of legacy codebases 
or projects that were initially developed without a strong emphasis on automated testing. 
It allows developers to incrementally add tests to existing code, reducing the 
risk of introducing regressions or breaking existing functionality while increasing 
confidence in the codebase.

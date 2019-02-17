An Introduction to the Tools
============================

## Test Fixtures
A *test fixture* is the fixed state that exists at the start of a test. A tes fixture ensures that a test is repeatable -- every time a test is run it starts in the same state so it should produce the same result.

All tests defined in the same class start with an identical fixture and may modify that fixture as they run.

## (jMock2): Mock Objects
A mock library creates mock objects dynamically, so you don't have to write your own implementations of the types you want to mock. It also provides a high-level API for specifying how the objet unders test should invoke the mock objects it iteracts with, and how the mock objects will behave in response.

The test runner automatically calls the mockery at the end of the test to check that all mock objects have been invoked as expected.

Expectations are our *definition of success*.

The moment we excercise the *system under test* models the outside event that triggers the behavior we want to test.

Test with mocks may not require any assertions.

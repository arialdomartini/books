# Introduction

## Testing
We test and we test some more, until we cannot prove there are still bugs in the software. Tradictionally, this testing occurs after the software is complete. As a result, it is a way of measuring quality -- not a way of building quality into the product. In many organizations, testing is done by someone other than the software developers.

## Automates Testing
### The "Fragile Test" Problem
Test automation using "record and playback" tools has some pitfals:

* behavior sensitivity
* interface sensitivity
* data sensitivity
* context sensitivity

### Behavior Sensitivity
If the behavior of the system is changed (e.g. the requirements are changed and the system is change to meet the new requirements), and tests that exercise the modified functionality will most likely fail when replayed.

### Interface Sensitivity
Testing the business logic inside the SUT via the user interface is a bad idea. Even minor changes to the interface can cause tests to fail.

### Data Sensitivity
All tests assume some starting point, called **test fixture** (or pre-conditions, or before picture). If the data changes. the tests may fail unless great effort has been expended to make them insensitive to the data being used.

### Context Sensitivity
The behavior of the system may be affected by the state of things outside the systems. These external factors could include the state of devices (printers, server), other applications, or even the system clock.


## Patterns
### Patterns versus Principles versus Smells

The book includes 3 kinds of patterns:

* **Strategy**-level patterns have far-reaching consequences (e.g. the decision to use Shared Fixture rather than Fresh Fixture takes us down a very different path and leads to a different set of test design patterns).

* **Design**-level patterns are used when developing tests for specific functionalities. The focus on how we organize the test logic (e.g. the use of Mock Objects)

* Test **coding idioms* describe different ways to code a specific test. Most of them are language specific (e.g. block closures for Expected Exception Tests, or Simple Success Tests)

## Refactoring
Refactoring is a highly disciplined approach to changing the design without changing the behavior of the code. It goes hand-in-hand with automated testing because it is very difficult to do refactoring without having the safety net of automated tests to proe that you have not broken anything during the redesign.

Refactoring tests differ a bit from refactoring production code because we do not have automated tests for our automated tests. To address this issue, many test refactorings are very conservative.

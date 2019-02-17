What Is the Point of Test-Driven Development?
=============================================

Developers often don't completely understand the technologies they're using. They have to learn how the components work *whilst* completing the project. Even if they have a good understanding og the technologies, new applications can force them to unfamiliar corners.

## Feedback Is the Fundamental Tool
The best approach a team can take is to use *empirical feedback* to learn about the system and its use, and then apply that learning back to the system.

Every time a team deploys, its members have an opportunity to check their assumptions against reality. Without deployment, the feedback is not complete.

We apply feedback cycles at every level of development, organizing projects in a system of nested loops ranging from seconds to months such as pair programming, unit tests, acceptance tests, daily meetings, iterations, releases and so on. The nested feedback loops reinforce each others.

Each feedback loop addresses different aspects of the system and development process. The inner loops are more focused on the technical detail. The outer loops are more focused on the organization and the team.

## Practices That Support Change

1. We need constant testing to catch regression errors. For systems of any interesting size, frequent manual testing is just impractical.
2. We need to keep the code as siple as possible. Developers spend far mor time reading code than writing it, so that's what we should optimize for. Simplicity takes effort.

TDD turns testing into a *design activity*. As Kent Beck described it to us

> "I was finally able to separate logical from physical design"

## Test-Driven Development in a Nutshell

As we develop the system, we use TDD to give us feedback on the quality of both its *implementation* ("Does it work?") and *design* ("Is it well structured?").

*Writing* tests:

* makes us clarify the acceptance criteria
* encourages us to write loosely couple components
* adds an executable description of what the code does
* adds to a complete regression suite

*Runnign* tests:

* Detects errors
* Discourage "gould plating" and unnecessary features

### Refactoring. Think Local, Act Local
The point is to improve the code so that it's a better representation of the featurs it iplements, making it more maintainable.

Each refactoring is small enough to be easy to undestand and "safe".

Refactoring is a "microtechnique" that is driven by finding small-scale improvements. Our experience is that, applied rigorously and consistently, its many small steps can lead to significant structural improvements. Refactoring is not the same acrivity and *redesign*, where the programmers take a conscious design to change a large-scale structure.


## The Bigger Picture
We've seen projects with high-quality, well unit-tested code that turned out not to be called from anywhere, or that could not be integrated with the rest of the system and had to be rewritten.

When we're implementing a feature, we start by writing an *acceptance test* which exercise the functionality we want to build.

Write a failing acceptance test => while() { write a failing unit test => make the test pass => refactor  }

The outer test loop is a measure of demonstrable progress. Acceptance tests often take a while to make pass, certainly more than one check-in episode, so we usually distinguish between cceptance tests we're working on (which are not yet included in the build) and acceptance tests for the feature that have been finished (which are included in the build and must always pass).

## Testing End-to-End
Whenever possible, an acceptance test should exercise the system end-to-end without directly calling its internal code. An *end-to-end test* interacts with the syste only from the outside.

For us, *end-to-end* means more than just interacting with the system from the outside -- that might be better called "edge-to-edge" tesing. We prefer to have the end-to-end test exercise both the system *and* the process by which it's built and deployed. An automated build, usually triggered by someone checking code into the source repository, will:

* check out the latest version;
* compile and unit-test the code
* integrate and package the system
* perform a production-like deployment into a realistic environment
* exercise the system through ints eternal access points.

Many of the steps might be fiddly and error-prone, so end-to-end build cycle is an ideal candidate for automation.

A system is *deployable* when the acceptance test all pass.




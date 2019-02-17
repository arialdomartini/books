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

## Levels of Testing
We build a hierarchy of tests that correspond to some of the nested feedback loops we described above:

* **Acceptance**: does the whole system work?
* **Integration**: does our code work against code we can't change?
* **Unit**: do our object do the right thing, are they convenient to work with?

The important thing is to ve clear about our intentions. 

* We use "acceptance tests" to help us, with the domain experts, understand and agree on what we are going to build next.

* We use the term "integration tests" to refer to the tests that check how some of our code works with code from outside the theam that we can't change.


## External and Internal Quality
There's another way of looking at what the tests can tell us about a system. We can make  distinction between external and internal quality: 

* *External quality* is how well the system meets the needs of its customers and users (is it functional, reliable,, available, responsive, etc.)
* *internal qualiry* is how well it meets the needs of its developers and administrator (is it easy to understand, easy to change etc.)

Everyone can understand the point of exernal quality; it's usually part of the contract to build.

Unit tests don't give us enough confidence that the system as a whole works. 

For a class to be easy to unit-test, the class must have explicit dependencies that can easily be substituted and clear responsibilities that can esasily be invoked and veriried. In software engineering terms, that means that the code must be *loosely coupled* and *highly cohesive* -- in other workds, well designed.

When we've got this wrong -- when a class, for example, is tightly coupled to distan parts of the system, has implicit dependencies, or has too many o unclear responsibilities -- we find unit tests difficult to write or understand, so writing a test first gives us valuable, immediate feedback about our design. Like everyone, we're tempted not to write test when our code makes it difficult, but we try to resiste. We use such difficulties as an opportunity to investigare why the test is hard to write and refactor the code to improve its structure. We call this **listening to the tests**.

### Couplign and Cohesion

* Elements are *coupled* if a change in one forces a change in the other.
* An element's *cohesion* is a measure of whether its responbilities form a meaningful unit. For example, ,a class that parsesot dates and URLs is not coherent, because they're unrelated concepts. A the other exteme, a class that parses only the punctuation in a URL is unlikely to be coherent, because it doesn't represent a whole concept.

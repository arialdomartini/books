Kick-Starting the Test-Driven Cycle
===================================

Action always generates inspiration.<br />
Inspiration seldom generates action.

## Introduction
An acceptance test must run end-to-end to give us the feedback e need about the system's external interfaces, which means we ust have implemented a whole automated build, deploy, and test cycle. This is a lot of work to do before we can even see our rist test file.

It flushes out the "unknown unknown" technical and organizational risk so they can be addressed while there's still time.

The risks of leaving it to later are just too high.

## First, Test a Walking Skeleton (Early End-toEnd Testing)
We can cut through the "first-feature paradox" by splitting it into two smaller problems.

* First, work out how to build, deploy and test a "walking skeleton"
* then use that infrastructure to write the acceptance tests for the first meaningful feature.

After that, everything will be in place for test-driven development of the rest of the system.

A "walking skeleton" is an implementation of the thinnest possible slice of real functionality tha we can automatically build, deploy and test end-to-end. It should include just enough of the automation, the major components, and communication mechanisms to allow us to start working on the first feature. We keep the skeleton's application functionality so siple that it's obvious and uninteresting, leaving us free to concentrate on the infrastructure.

It's also important that "end-to-end" requires to *deploy it into a production-like environment*. This is critical for 2 reasons:

* First, this is the sort of error-prone activity that should not be done by hand, so we want our scripts to have thotoughly exercises by the time we have to deploy for real. Nothing forces us to understand a process better than trying to automate it.
* Second, this is often the moment where the development team bumps into the rest of the organization and has to learn how it operates.

### The Importance of Early End-to-End Testing
Because the need for end-to-end testing has influenced its design, the system won't be diffucult to test.

## Deciding the Shapr of the Walking Skeleton
Our rule of thumb is that we should be able to draw the design for the "walking skeleton" in a few minutes on a whiteboard.

Any ideas we have in the first steps are likely to be wrong, so we prefer to discover those details as we grow the system. We're making the smallest snumber of decisions we can to kick-start the TDD cycle, to allow us to start learning and improving from real feedback.

## Build Source of Feedback
We have no guarantees that the decisions we take about the design are right. The only thing we can rely on is validating them as soon as possible by building feedback into our process.

## Expose Uncertainty Early
The time to implement the fist few features will be inpredictable as the team discovers more about its requirements and target environment.

The result is that experiences stakeholders react badly to the instability at the start of an incremental project because they expect that the end of the project will be much worse.<br />
Our experience is that a well-run incremental development runs in the opposite direction.

A "walking skeleton" will flush our issues early in the project when there's still time, budget and goodwill to address the uncertainty.

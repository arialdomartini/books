Maintaining the Test-Driven Cycle
=================================

## Start Each Feature with an Acceptance Test
We write the acceptance test using only terminology fro the application's domain. We find that writing such a test before coding makes us clarify what we want to achieve. Starting with tests makes us look at the system from the users' point of view.

## Separate Tests That Measure Progress from Those That Catch Regression
We organize our test suites to reflect the different roles that the tests fullfill

* Unit and integration tests support the development team, should run quickly and should always pass.
* Acceptance tests for completed feature catch regressions and should always pass, although they might take longer to run.

If requirements change, we must move any affected acceptance tests out of the regression suite back into the in-progress suite, edit them to reflect the new requirements and change the system to make them pass again.

## Start Testing with the Simplest Success Case
Degenerate cases don't add much to the value of the system and, more importantly, don't give us enough feedback about the validity of our ideas.

We prefer to start by testing the simplest *success* case.

## Write the Test That You'd Want to Read
We know we've implemented enough og the supporting code when the test fails in the way we'd expect, with a clear error messages describing what needs to be done.

## Whatch the Test Fail

## Develop from the Inputs to the Outputs
It's tempting to start by unit-testing new domain model objects and the trying to hook them into the rest of the application. It sems easier at the stat -- we feel we're making rapid progress working on the domain model when we don't have problems later. Wel'll have wasted time building unnecessary or incorrect funcionality, because we weren't receiving the right kind of feedback when we were working on it.

## Unit-Test Behavior, Not Methods

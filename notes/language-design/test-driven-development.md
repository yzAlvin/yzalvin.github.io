---
layout: post
title: Test Driven Development
date: 2021-03-23
permalink: /notes/language-design/test-driven-development
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Articulates what a test first approach is, why it is useful and the high level red, green, refactor pattern. |
| L2	| Methods/Classes are written in a way that they are unit testable however the tests are largely written post the actual method/class being written. |
| L3	| 	The basic TDD cycle is followed where in general each time new functionality is added to the solution an appropriate test is written first.  |
| L4	| Code is driven by a test first approach. Able to apply discretionary judgement on when to use a top down or bottom up test approach. Able to identify short term tests that help with implementation vs long term tests that prove validity of solution. |

## What is it?

Test Driven Development is writing tests first before the actual code, and then continually running them to make sure every new feature adds new functionality as well as preserves old functionality.

The whole point is to wear different hats
* testing perspective
* developer perspective
be able to think differently

Think about how to test the problem before how to implement it.

A useful pattern to help with TDD is Red-Green-Refactor ..

Red-Green-Refactoring Pattern:
* Write a failing test
* Write code to pass Test
* Refactor code to meet standards
* Repeat!!

Basically, a bottom-up approach works from the specifics to the general, while a top-down approach goes from the general to the specifics.

Top-down approaches emphasise planning and a complete understanding of the system. No coding begins until a sufficient level of detail has been reached in the design of at least some part of the system. These are implemented by attaching stubs in place of the module. However, delays testing ultimate functional units of a system until significant design is complete.

Bottom-up emphasizes coding and early testing, which begins as soon as the firt module has been specified. Runs the risk that modules may be coded without having a clear idea of how they link to other parts of the system, such linking may not be as eary as first thought.

Modern software design approaches usually combine both.

### Bottom Up Approach

Writing smaller independent classes first, because the higher-level classes depend upon them.

Progressively generalsing the code base as tests become increasingly specific.

Usually avoids mocks, but still uses them when neeed.

Bad abstractions leads to problems, it is sort of like *guesswork*. You are guessing which small classes/code you will need before you actually need it. Code is wasted if you guessed wrong or you might even overshoot and implement unnecessary methods that are never used by higher-level classes.

### Top Down Approach

Progressively implement increasing functionality, one section at a time.

Usually a reliance on mocks is required to simulate the functionality of lower level components. 

Basic Top-Down Workflow:

1. Ask what the whole thing is supposed to do

2. Write a test for the top-level interface by using code you wished exisetd. You decide what interface you want before writing the implementation.

3. Experiment with different designs

4. Run the test, fix the errors, repeat until test pass. Errors will tell you what you need to write next.

5. Repeat!! if the overall design is done, switch to unit tests

---------------------------------------------------------


I guess both approaches have their pros and cons, I lean towards bottom up since I'm not too confident with mocking yet, something I need to work on..


However I should try top down, as it results in simpler, highly cohesive, strongly decoupled code, that is more readable and therefore, maintainable.

Short term tests that help with implementation (smaller unit tests) 
long term tests that prove validity of solution (behaviour tests, testing logic and flow of solution)

## Why

* Using TDD ensures testing.
* Drives the design of a program.
* Focusing on tests first means we must imagine how functionality is used.
* Ensures all written code is covered by at least one test.
* Leads to confidence in code.
* Catch defects early in the development cycle. (Easier to fix early)
* Can lead to more modular, flexible, and extensible code.
* Smaller, more focused classes, looser coupling, and cleaner interfaces.
* Use of mocking contributes to modularisation as it requires module be able to switch between mock versions for testing, and real versions for deployment.
* No more code than necessary is written to pass a failing test case, eg. no need for an else branch unless their is a test that motivates it.

## Who

## When

## Where

TDD is not sufficient where full functional tests are required. eg. user interfaces, databases.

## How

# Before Coding

## Understand the problem, try not to think about the implementation

## Tasking
* List all the scenarios
* Scenarios should relate to the problem, not the steps to solve the problem
* Solving all scenarios should solve the problem

## Design the interface
* The interface should focus on the problem instead of steps in the solution
* Find out the minimal required inputs to solve the problem
* Find out the output

## Design Test Cases
* Test cases should be specific
* From the simplest
* Just enough to start, does not need to cover all scenarios

Do not think about implementation at all, only testing. Do not worry about the steps
We are creating a safe net for refactoring, if we test implementation details, if we change implementation but the behaviour remains the same, tests will still fail.

Difference between scenario and test case
Scenarios are very high level, split into as small components as possible.

KISS

YAGNI

"Fake it till you make it"

Write tests first.
Keep the unit tests small. 
* Reduced debugging effort - When a test fails, smaller units helps in finding errors.
* Self-documenting tests - Small tests are easier to read and understand.

### Best Practices

* Test Structure
	* Setup
	* Execution
	* Validation
	* Cleanup

* Avoid tests depending on state from previous tests
* Avoid dependencies between tests
* Avoid testing precise execution behavior timing or performance
* Avoid testing implementation details
* Avoid slow tests
* Map test files to class files

* Tests should:
	* Increase readability
	* Be self-documenting
	* Increase confidence the code **works**


- Test requirements, not low level
- Test public API. Given when then
- Test the exports from a module
- Focus on higher-level
- Test modules, not class
- Refactoring is needed to see what is implementation and what is exports from module
- Test behaviours
- Think about your code as an api
- Test the abstraction, not the implementation
- Test are isolated and with shared fixture (to run quickly)
- Red-green-refactor (go fast to working code)
- No new tests during refactoring
- Heavy coupling is the problem with all software
- Thin public api
- Refactoring = changing internals
- Patterns in the refactoring
- If you're not really sure, write tests for implementation (delete the tests)
- Not classes, behaviours
- Don't isolate classes in testing
- Private methods (these are implementation details)



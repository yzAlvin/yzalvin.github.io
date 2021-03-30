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

I only have experience writing unit tests, and I guess manual testing.

Test Driven Development is writing tests first before the actual code, and then continually running them to make sure every new feature adds new functionality as well as preserves old functionality.

A useful pattern to help with TDD is Red-Green-Refactor ..

Red-Green-Refactoring Pattern:
* Write a failing test
* Write code to pass Test
* Refactor code to meet standards
* Repeat!!

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

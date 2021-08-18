---
layout: post
title: Test Doubles
date: 2021-03-23
permalink: /notes/language-design/test-doubles
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Articulates what a basic test doubles is and why it is important. Able to explain the high level differences between various types of test doubles (mocks, stubs, fakes, etc). |
| L2	| Able to write their own basic test doubles without using a testing framework. Able to swap out parts of the solution code base with appropriate custom written test doubles to isolate behaviour for testing |
| L3	| Leverages a test framework to utilize out of the box test doubles. Can articulate what type of test double the test framework is providing for different test scenarios. Able to swap out parts of the solution code base with appropriate test double framework implementations to isolate behaviour for testing |
| L4	| Has a deep understanding of what test doubles are and why they are important and able to apply this to code. Able to explain with examples the differences between various types of test doubles. Can make appropriate judgement calls on when to use framework test doubles vs writing own. |

## What is it?

Test doubles are used to replace production objects/functions to isolate items under test from the implementation of their dependencies.
They are helpers that make it possible to control dependencies, so that the unit under test can be tested under certain circumstances.

### Subs
Return hard coded values, they ensure the returned value is always the same.

Focuses on state of the dependency

### Mocks
An implementation of the contract, and can also record arguments and if and how many times a method was called

Focuses on behaviour of the dependency

### Fakes
An object with working implementations, but implementation is usually not suitable for productions

### Dummies
Contain no logic and no return values. Usually just used to fill a parameter

### Spies
Listens to methods to see if it was called and how many times. Like a mock.

## Why

They provide a means of keeping tests fast by removing slow running dependencies (generally IO) like databases, web servers and file systems.

They are also useful in unit tests, an example is a function that returns a timestamp.

Because it is not a "pure" function (it does not always return the same thing when it is called), we need some way to test it. We can use a mock to test it does what we expect when we supply it some value.

The unit we are testing can be tested in full isolation if all dependencies are test doubles.
They are also great to trigger hard-to-create scenarios.

## Who

## When

## Where

## How

Often facilitated by dependency inversion.

Writing your own basic test doubles without a testing framework.

Using a framework like Moq in C#

There is not a huge difference between using a mocking framework and writing implementations. You can accomplish the same thing (testing your code) it is just about the means to do it.

Mocks require a framework. Not a big deal, just installing a package. You will also have to learn the framework, investing time in it. Might have to redo the time investment if you switch frameworks. Writing your own implementations is just using the programing language natively. Learning curve is smaller and perhaps more intuitive if you use test implementations.

However test implementations bloats the code base. Often they ase just stubs, hard to see why you would want to have an extra class. - with mocks, they reside within the test method and configured in this scope. It can make it hard to understand what is going on in the test, but in scenarios where the amount of logic is small, it is good the setup is in the code, so you don't need to open other classes.


-    Mocks require a framework
-    You have to learn and master the mocking framework (invest time)
-    Using mocks you avoid having extra test double classes for your tests
-    Setting up mocks and their expectations can take up a lot of space in your tests
-    With mocks, the expected behavior of your dependencies is within in your test - not in separate classes

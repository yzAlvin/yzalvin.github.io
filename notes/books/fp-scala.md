---
layout: post
title: Functional Programming in Scala
date: 2021-05-04
permalink: /notes/books/fp-scala
---

* Functional programming is "programming with functions"

* Pure functional programming restricts functions to be as they are in mathematics: binary relations that map arguments to results.

* Scala is an impure functional programming language, in that it admits impure as well as pure functions, and does not try to distinguish between them by giving them different syntax or different types.

* Side effects such as mutations, I/O, or use of exceptions are not ruled out, but overusing them is generally not considered good style.

## Side Effects
A function has a side effect if it does something other than simply return a result

* Modifying a variable
* Modifying a data structure in place
* Setting a field on an object
* Throwing an exception or halting with an error
* Printing to the console or reading user input
* Reading from or writing to a file
* Drawing on the screen

Pure functions increases modularity, easier to test, reuse, parallelize, generalize, and reason about.

Referential Transparency and the Substitution Model.

Pure functions are easier to reason about.

A function f with input type A and output type B (written in Scala as a single type A => B) is a computation that relates every value a of type A to exactly one value b of type B such that b is determined solely by the value of a.

For an expression to be referentially transparent, the expression can be replaced by its result without changing the meaning of our program.

A function is pure if calling it with RT arguments is also RT

* Tail recursive functions
* Higher order functions

A call is said to be in tail position if the caller does nothing other than return the value of the recursive call.
If all recursive calls made by a function are in tail position, Scala automatically compiles the recursion to iterative loops that don't consume call stack frames for each iteration.

By default, Scala doesn't tell us if tail call elimination was successful, but if we're expecting it for a recursive function we write, we can use the `tailrec` annotation so it can give a compile error if it's unable to eliminate the tail calls of the function.

When we define a function literal like (a, b) => a < b, this is really syntactic sugar for object creation:
val lessThan = new Functions2[Int, Int, Boolean] {
	def apply(a: Int, b: Int) = a < b
}


trait is an abstract interface that may optionally contain implementation of methods
sealed means all implementations of the thing must be declared in the file.

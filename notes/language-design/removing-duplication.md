---
layout: post
title: Removing Duplication 
date: 2021-03-23
permalink: /notes/language-design/removing-duplication
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Articulates conceptually the different forms of duplication (code duplication, domain duplication) |
| L2	| Able to identify basic repeatable duplication in code although struggles to extract duplication patterns into appropriate methods/classes OR is able to extract duplication if pattern is identified by someone else but struggles to identify duplication on their own. |
| L3	| Repeatable patterns are identified based on code duplication. Duplicate code patterns are consistently pulled out into supporting methods or classes. |
| L4	| Able to articulate in depth the difference between domain duplication and code duplication. Consistently identifies and removes domain duplication. |

## What is it?

When there are repeated chunks of code or code that does very similar things, there may be a case of code duplication.

Code Duplication

Domain Duplication

## Why

We want to remove duplication as when a requirement changes we will need to make a change EVERYWHERE there is duplication, this can get messy and tedious, and it is easy to overlook parts.

Removing duplication will also make things smaller, neater, more readable ==> more maintainable.

## Who

## When

> "Duplicate code always represent a missing abstraction." 

## Where

## How

Extract duplicate patterns into appropriate methods/classes
Polymorphism

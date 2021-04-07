---
layout: post
title: Object Composition
date: 2021-03-23
permalink: /notes/language-design/object-composition
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Articulates what object composition and inheritance are. Articulates the benefits of object composition over inheritance. |
| L2	| Can implement inheritance in coding problems. |
| L3	| Can implement object composition in coding problems. Consistently applies composition over inheritance in code. |
| L4	| Can confidently make trade-offs on when to use inheritance and when to use object composition in code. Can articulate those trade-offs with others. |

## What is it?

Object composition is useful for when we want to share functionality between multiple classes, and inheritance is not a good solution.

Inheritance is when you design types around what they ARE

Composition is designing around what they DO


## Why

Composition is more maintainable than inheritance. It also helps to keep the size of the project smaller and (objectively) neat.

## Who

## When

One way to remember when to use either is:
If there is a 'has a' relationship we could use composition
If there is a 'is a' relationship we could use inheritance

But like with everything else don't stick to rules without critical thinking.

## Where


## How

Instead of creating a single parent class:

1. Create one more more smaller classes or interfaces that encapsulate the desired functionality
2. Include instances of these in any new classes we wish to share functionality with
3. Expose the desired functionality by using these instances

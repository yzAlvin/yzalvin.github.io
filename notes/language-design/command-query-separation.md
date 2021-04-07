---
layout: post
title: Command Query Separation 
date: 2021-03-23
permalink: /notes/language-design/command-query-separation
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Articulates at a high level what command query separation is. |
| L2	| Can identify and provide examples of command methods and query methods in code. Can identify in code methods that violate command query separation. |
| L3	| Generally applies command query separation when writing methods. |
| L4	| Consistently applies command query separation in code. Identifies exceptions to the general rule and can articulate trade-offs with others. |

## What is it?
Command Query Separation is a principle of imperative programming.

Every method should either be a:
* **command** that performs an action
* **query** that returns data to the caller

but not both.

## Why


## Who

## When
There are some exceptions, for example, the `pop` method of a stack datastructure both performs the action of removing the top element of the stack, but also returns the removed element.

## Where

## How

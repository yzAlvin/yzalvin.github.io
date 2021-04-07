---
layout: post
title: YAGNI 
date: 2021-03-23
permalink: /notes/language-design/yagni
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Articulates at a high level what YAGNI means and why it is important |
| L2	| Can identify in code when YAGNI has been violated. |
| L3	| Generally applies YAGNI principles when solving problems. Delays implementing code capabilities to support presumptive features. Solution design focusses on solving the problem at hand without gold-plating. |
| L4	| Articulates the concept of YAGNI at a deep level. Effectively differentiates between code that supports presumptive features and code that is structured to make software easier to modify. |

## What is it?

YAGNI stands for "You aren't gonna need it".
It boils down to avoid adding functionality until it is necessary.
This results in the fewest lines of code that still meets the requirements.

## Why

YAGNI is useful, because requirements may change in the future, so code that is not used could stay useless anyway or the feature it was intended for may never be necessary.

There would be more refactoring required later if there is some code that was not initially being used and is now being used to fit a new requirement.

There are costs to adding in the unnecessary code:

* Cost of delay - could have been working on another, necessary feature.
* Cost of build - time was spent on a currently useless feature
* Cost of repair - time spent needing to fix the code
* Cost of carry - unnecessary space used up by code, another thing to read

## Who

## When

## Where

## How

Only implement the bare minimum, this is linked to keeping things small

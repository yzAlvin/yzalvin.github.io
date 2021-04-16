---
layout: post
title: Code Smells
date: 2021-04-07
permalink: /notes/code-smells
---

## What is it?

Code smells, sign that something is off, usually getting rid of the smell will make code more maintainable.

* Names - not too long or short
* Bloated methods - break behaviours into separate methods
* Excessive parameters - look for common data groupings
* Excessive return data - look for common data groupings
* God lines - look for actions that can be broken apart

Focus on **what** code does, instead of **how** it does it.
Find the core purpose of methods
Find the sweet spot for naming conventions

* Oversized classes / God objects - break them up into smaller classes
* Undersized classes - maybe they aren't encapsulating much data. Consider incorporating into another class

* Feature Envy - When a class uses methods from another class - Leads to dependency and brittle code. 
	* Look closely at the class dependency
	* consider transferring code to a dependent class or refactoring to share class members 
	* consider dependency injection 

* Inappropraite Intimacy - Class is dependent on another class' implementation - When a class references private members of another.
	* Refactoring code or creating a shared implementation

* Literal Usage - Hard coded values lead to errors and make modifications difficult
	* Make constants, even better would be to store in a resource file or external database
	
* Data clumping - passing around the same privmitive data values
	* Create object or data model and pass that instead

Think of classes as individual and self-sufficient

* Shotgun surgery - So much duplicated code you need to make changes in multiple locations

* Contrived complexity

## Design Smell Categories
* Abstractions
* Encapsulation
* Modularisation
* Hierarchy

### Abstractions

#### Missing Abstractions

Literals and encoded strings are used instead of a data model
Referred to as data clumping and primitive obsession
Group primitive data types into their own abstractions

#### Multifaceted Abstractions

Happens when abstraction has more than one responsibility

#### Duplicate Abstractions

Classes or interfaces with same name and/or behaviour
Look for similar responsibilities and refactor into single abstraction

#### Incomplete Abstractions

Class or interface doesn't fully support a responsibility
Can happen when parent classes have optional or overridable methods
Derived classes aren't forced to fully implement their responsibility

### Encapsulation

#### Deficient Encapsulations

Happens when abstractions implementation and/or members are exposed or poorly protected
Leads to data vulnerability and behaviour misuse
Solution is to ensure abstractions are only as accessible as they need to be

#### Unrestrained Encapsulation

Arises when abstraction's state is globally visible
Can lead to even more severe data corruption and behaviour abuse
Avoid global accessibility

#### Unexploited Encapsulation

When client code uses if-else or switch statements to check object's type instead of exploiting existing type variation
Lookout for long switch statements that fire different behaviours for different object types
Use polymorphic methods in the object and decouple client code from object type checking

### Modularisation

#### Insufficient Modularisation

When an abstraction has not reached its ideal decomposition
Can show itself in deeply nested class hierarchies or bloated classes
Look for na abstraction's base or core purpose and decompose its code to that level of detail

#### Broken Modularisation

Show up when data or methods that should be grouped together are spread out across multiple abstractions
Similar to data clumping, just includes methods instead of only primitive types
Focus on refactoring together like-minded behaviours and information

#### Cyclically Dependent Modularisation

Happens when abstractions are heavily dependent on each other and become tightly coupled
Can be direct or indirect dependency - a higher-level take on feature envy and inappropriate intimacy code smells
Refactor out dependent code or use dependency injection to decouple implementations

### Hierarchy

#### Polygon Hierachy

Base abstractions repeatedly inherited form a polygon shape
Remove redundant inheritance to streamline abstraction hierachy

#### Broken Hierarchy

Smells when a base abstraction and a derived abstraction don't share an IS-A relationship as they should
Happens most often when inheritance is used instead of composition
Particularly dangerous as it allows shared behaviours
Replace inheritance with composition or delegation structure

#### Complex Hierarchy

Identify the smell by excessively tangles hierarchy graphs or maps
These tend to be too wide, too deep, too imbalanced, or all three
Prevalent in code bases that are passed from developer to developer
Decompose complex hierarchies

#### Cyclic Hierarcy

Found anywhere a super type references or is dependent on a subtype
This can be a super type containing a subtype objct, referencing a subtype name, or using subtype members
There references can be direct or indirect
Completely refactor out dependent code

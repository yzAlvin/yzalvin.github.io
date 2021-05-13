The whole point is to wear different hats
testing perspective
developer perspective
be able to think differently

How to test the problem before how to implement it.

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

Refactoring step is when we apply the 4 rules of simple design

Difference between scenario and test case
Scenarios are very high level, split into as small components as possible.

Scenarios
* A cell can be alive or dead
	* Live -> Dead - size: (w: 5, l: 5), (liveCells: [(2, 2)]) - size: (w: 5, l: 5), (liveCells: [])
	* Live -> Live - size: (w: 5, l: 5), (liveCells: [(2, 2), (1, 2), (3, 2)]) - world.liveCells include (2, 2)
	* Dead -> Live - size: (w: 3, l: 3), (liveCells: [(0, 0), (0, 1), (1, 1)]) - world.liveCells include(1, 0)
	* Dead -> Dead

Neighbours
* Cell has 8 neighbours
* The cell is on the edge
	* Cell wraps around
* The cell is not on the edge

* World Size does not change - size: (w: 3, l: 4), (liveCells: []) - size (w: 3, l: 4), (liveCells: [])

Exceptions
* 


Test Cases


If you can remove some code and the tests still pass, remove that code.

When writing interfaces, try not to use self defined types, be explicit about types
We should not be changing the interfaces later on

new World(size: (int length, int width), liveCells: List<(int x, int y)>).nextGeneration() => World


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

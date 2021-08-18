---
layout: post
title: "First Post"
date: 2021-03-17 09:52:00 +1100
---
Hello, 

I started this to take a bit of a break from coding, and to have a place to keep notes, practice markdown, and maybe learn ruby. 

I was heavily inspired by many other developer blogs like peter collingridge, project nayuki and many others.
I don't really expect anyone to read my notes except myself.

# Practice Markdown
## Stuff about me maybe:

* colemak keyboard layout
* 40% ortholinear keyboard
* triathlon
* chess casually
* board games (**coup**)

## I want to be better at:

1. cooking
2. cycling
3. swimming
4. *vim*
5. chess
6. Linux 

![Tux, the Linux mascot](https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/Classic_flat_look_3D.svg/155px-Classic_flat_look_3D.svg.png)

A really great quote I heard someone say at work was 
 > “If you don't ask, the answer is always no.”

I think it changed my mindset a little bit about asking for help.

> Compare Yourself To Who You Were Yesterday, Not To Who Someone Else Is Today

I've been interested in declarative programming ever since I was shown an example of imperative vs declarative approaches to programming.

For example, 2 different ways to get even numbers from an array:

Imperative

	int[] array = [1, 2, 3, 4, 5];
	List<int> evenNumbers = new List<int>();
	foreach(int n in array)
	{
		if (n % 2 == 0)
		{
			evenNumbers.Add(n);
		}
	}
	return evenNumbers;

Declarative

	int[] array = [1, 2, 3, 4, 5];
	List<int> evenNumbers = array.Where(n => n % 2 == 0).ToList();
	return evenNumbers;

Okay sort of reaching just to include as much [markdown syntax](https://www.markdownguide.org/basic-syntax/) as I can so bye


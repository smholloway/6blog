---
layout: post
category: technology
tags: []
title: What School Never Taught You
---
{% include JB/setup %}

It's probably no surprise, but school does not prepare you for the real world. Sadly, competent Computer Scientist students--those who made good grades in school--may make poor professional programmers.

School examples are small, self-contained projects with a small or non-existent team.

## A more realistic example
Let's say you have a large software system with a sort method. A bug comes in related to sorting users--they're being sorted in ascending order by default. So you go fix the bug by flipping the comparator from less than to greater than. You update the unit test to expect descending order, run the tests, and check-in after seeing your user sorting "works." Your continuous integration system kicks off a build, and there are a number of bugs throughout the product. Long story short, other parts of the product relied on the sort being descending. Worse still, there are entire subsystems built on the sort algorithm--it is used everywhere! The straightforward approach in one area broke other areas. Perhaps it would have been better to create a second sort method with a flag for ascending or descending; existing calls would still work, but the user sorting can be transitioned to the new, differentiated sort. Well, this adds complexity to the system by adding another method. You could refactor sort to also take a parameter, but then you have to update every reference to the new method and add the correct default parameter. There are many other possibilities, and it might be that your understanding of the system is insufficient for finding the best solution.

Half-knowledge and quick action combined over numerous people and many years lead to a beast of a system that will take years to grok. Formerly fun programming becomes tedious hide-and-go seek debugging--a very different skill. Projects need a starter, a finisher, a debugger, and an architecture [[http://jacquesmattheij.com/The+Starter+the+Architect+the+Debugger+and+the+Finisher]], but you are unlikely to be hired as any one of those.

### What to do about it
Work in a single repository with at least 5 other people committing.
Debug your teammate's code, or have them check-in on top of you and create a bug.


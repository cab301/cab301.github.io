---
layout: default
title: Assignment 1
nav_order: 1
parent: Assignment FAQ
permalink: /faq/assignment-1
---

# Assignment 1: Abstract Data Types
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

## Are there any limits on the report size?

Try to keep the report concise and to the point. There is no word limit, but we should be able to find the relevant information quickly, so make sure that it is formatted nicely.
We don't expect you to use any particular style. That part is left up to you.

## Is it fine to make our own helper methods?

Only if they are private methods.

## Can we use 3rd party libraries for testing and test documentation?

There shouldn't be an issue with that, as long as they don't appear in the submitted files.

## Are we expected to use selection, insert and bubble sort per algorithm or just use one for all of them?

Use whichever algorithm you believe is the most efficient.  It is fine to use the same algorithm if you wish.

You just need to choose what you think is the best algorithm and apply it to your work.  No need to use multiple algorithms.

## Is there a specific .NET version we have to use for the assignment or are we fine to go ahead and use .NET 7.x & C# 11?

It is fine to use .Net 7.X.

## Should the assignment 1 implementation leverage content from weeks 1 > 4 - I see there are more efficient algorithms for search such as quick sort, merge sort etc in week 6 content, but I assume we will have an opportunity to implement these search algorithms in assignment 2?

You won't get extra marks for using the week 6 algorithms over the ones covered in week 3.  Both are equally as good for the purposes of assignment 1.

## What type of unit testing are we meant to to produce? Is it just if/else -> console logging errors or do we need to build test classes?

You may use any method to test your programs that you wish.  The only things you need to submit for the assignment are the **completed class files** and the **report**.  Testing should be done for your own benefit and piece of mind only.  Markers will be using their own testing plan when grading the assignments.

## Regarding analysis and pseudocode.

We require the entire method you have written to be analysed for each of the algorithms, so the pseudocode in the report should look something like this:  `ALGORITHM ShortestJobFirst() ...`

We definitely do not want to see a copy and paste of the sorting algorithm used from the textbook.

What we want to see is the pseudocode and analysis for the entire scheduling algorithm and not just the sorting part.  We don't want a simple copy and paste from the textbook.  There is no real value in that.

It's perfectly fine to use algorithms from the textbook (in fact this is what we expect), but the task requires the pseudocode and analysis be of the entire method.
Also be sure to include all of your references.

For example: ALGORITHM ShortestJobFirst(), not just ALGORITHM BubbleSort(A[0..n-1]) because you might have used Bubble sort.  In this case your algorithm will be considered incomplete.

Some trivial functions, like how Swap is used in Selection sort, don't necessarily need to be expanded because there are only a few constant time operations.  But if in doubt, write every line explicitly to keep on the safe side.
---
layout: default
title: Writing Test Cases for Methods
nav_order: 1
has_children: true
permalink: /pracs
---

# Writing Test Cases for Methods
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

## Context: Testing A Method

A method is a block of code that performs a specific task, forming a unit of a program. This unit of code can be tested to ensure that it works as expected. This is done by providing a set of inputs to the method, and checking that the output is as expected.

Such a process is called **unit testing**, and the inputs and outputs are called **test cases**.

## What is a Test Case?

A test case is a set of inputs and expected outputs for a method. A test case is used to test a method to ensure that it works as expected. A test case is made up of the following components:

- **Description**: A description of what is being tested. This should include the name of the method being tested, and a general description of the inputs and outputs.
- **Inputs**: The specific inputs that are being provided to the method, as well as any preconditions that must be met before the method is called.
- **Outputs**: The expected outputs of the method, as well as any postconditions that must be met after the method is called.

## Some Guidelines for Writing Test Cases

- **Each test case should test a single method**: This is because a test case should be as simple as possible, and testing multiple methods in a single test case can make it difficult to determine which method is causing the test case to fail. *However, when it is impossible to test a method without calling another method (for example, when setting up the preconditions, or checking the postconditions), it is acceptable to call another method.*
- **Be specific**: The description of the test case should be as specific as possible, including the test data that is being used, and the expected output data.
- **Test both valid and invalid inputs**: This is because a method should be able to handle both valid and invalid inputs. For example, a binary search method should be able to handle the case where the search value is in, and not in, the array. It should also be able to handle the case where the array is not sorted.
- **Test boundary conditions**: This is because boundary conditions are often the source of errors in a program. For example, a binary search method should be able to handle the case where the search value is the first, last, or middle element of the array, or where the array is empty, or contains only one element.

## Common Test Cases

While there is no one-size-fits-all approach to writing test cases, there are some common test cases that can be used as a starting point. These test cases are listed below.

**_Disclaimer_**: **These test cases are not exhaustive, and should be used as a starting point for writing test cases. You should always consider the specific requirements of the method that you are testing, and write test cases that are appropriate for the method.**

### For Methods that Validate some Input

These methods are used to validate some input, and usually return a `bool` value.

- **Valid input**: The input is within the valid range, but is not at the boundary of the valid range.
- **Boundary valid input**: The input is valid, and is at the boundary of the valid range.
- **Invalid input**: The input is outside the valid range, but is not at the boundary of the valid range.
- **Boundary invalid input**: The input is outside the valid range, and is at the boundary of the valid range.

<details closed markdown="block">
<summary>
  <mark>
    Why should we test for the boundaries? (Click to expand)
  </mark>
</summary>

**Boundary valid input tests**

Consider the following method that validates if a number is between 18 and 35:


```csharp
public static bool IsValidAge(int age)
{
    return age >= 18 && age <= 35;
}
```

In this case, if the programmer forgets to include the `=` sign, the method will not work as expected. 

For example, if the programmer writes `return age > 18 && age < 35;`, the method will return `false` when the input is `18` or `35`, which is not what we want.

**Boundary invalid input tests**

The following method does the same thing, but written slightly differently:

```csharp
public static bool IsValidAge(int age)
{
    return age > 17 && age < 36;
}
```

In this case, if the programmer mistakenly writes `return age >= 17 && age <= 36;`, the method will return `true` when the input is `17` or `36`, which is again not what we want.

</details>

### For Collection Methods

These methods are used to perform some operation on a collection, such as adding or removing an element, or searching for an element, sorting the collection, converting the collection to an array, etc.

- **Empty collection**: The collection is empty.
- **Collection with one element**: The collection contains only one element.
- **Collection with multiple elements**: The collection contains multiple elements.
- **Collection with duplicate elements**: The collection contains duplicate elements.
- **Collection with null elements**: The collection contains null elements.
- **Full collection**: The collection is full, if there is a capacity.

## Example: Writing Test Cases for a Validate Age Method

The method below is used to validate if a person is between 18 and 35 years old:

```csharp
public static bool IsValidAge(uint age)
{
    return age >= 18 && age <= 35;
}
```

We can write the following test cases for this method:

| Test Case | Inputs | Expected Output | Notes |
| --------- | ------ | --------------- | ----- |
| IsValidAge given age is 14 | `age = 14` | `false` | Normal invalid input |
| IsValidAge given age is 17 | `age = 17` | `false` | Boundary invalid input |
| IsValidAge given age is 18 | `age = 18` | `true` | Boundary valid input |
| IsValidAge given age is 25 | `age = 19` | `true` | Normal valid input |
| IsValidAge given age is 35 | `age = 35` | `true` | Boundary valid input |
| IsValidAge given age is 36 | `age = 36` | `false` | Boundary invalid input |
| IsValidAge given age is 40 | `age = 40` | `false` | Normal invalid input |
---
layout: default
title: Workshop 4 - Basic Sorting Algorithms
nav_order: 2
has_children: false
permalink: /workshop-4
---

# Workshop 4: Basic Sorting Algorithms - Solutions
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

# Part A: Sorting Algorithms

---

## **Question 1**. Sorting Algorithms basics

State whether each of the following statements is true or false. If the answer is false, explain why.

a. In the **selection sort** algorithm, the **numbers of comparisons** for both sorted lists and random lists of the same size **are the same**, and the **numbers of moves** for both sorted lists and random lists of the same size **are the same** as well.

> **Answer**: True.
>
> Every iteration of the insertion sort algorithm involves two steps:
> 1. **Finding the next smallest element** in the unsorted portion of the list.
> 2. **Swapping** the next smallest element with the first element in the unsorted portion of the list. It is possible to **swap the element with itself**.
>
> As a result, the number of comparisons (to find the next smallest element), and the number of moves are the same for any list of the same size. We can see this in the pseudocode, where `A[j] < A[min]` and `swap` are always called.

b. In the **insertion sort** algorithm, the **number of comparisons** for **random lists** is **less than** the number of comparisons for **reverse order lists** of the same size.

> **Answer**: True.
>
> Every iteration of the insertion sort algorithm involves three steps:
> 1. **Finding the correct position** to insert the next element (a.k.a, key) by looking back through the sorted portion of the list, finding **the first element that is less than the key**.
> 2. **Shifting elements** in each move to make room for the key to be inserted.
> 3. **Inserting** the key immediately after the element found in step 1. If none found, insert at the beginning of the list.
>
> In a **reverse order list**, the key will always be compared with every element in the sorted portion, and inserted at the beginning of the list. This results in the maximum number of comparisons (and moves).

c. In the **bubble sort** algorithm, the **number of moves** for **partially sorted** lists is less than the number of moves for **random lists** of the same size.

> **Answer**: True
>
> The bubble sort algorithm involves **comparing adjacent elements** and **swapping** them if they are in the wrong order. Having the list partially sorted means that more elements are already in the correct order, hence fewer swaps are needed to sort the list.

---

## **Question 2**. Bubble Sort worst-case scenario

Find an array that makes the bubble sort exhibits its worst behaviour.

> **Answer**: The worst-case scenario occurs when the comparison `A[j + 1] < A[j]` is always true (i.e., each number is larger or equal to the next, or that **the list is sorted in reverse order**).

---

## **Question 3**. Sorting Algorithms by Hand

Draw a sequence of diagrams to illustrate how each of the following algorithms sorts the given array. Show full details to illustrate your understanding of the algorithm

| Index (i) | 0 | 1 | 2 | 3 | 4 | 5 |
|-----------|---|---|---|---|---|---|
| x[i]      | 30 | 50 | 70 | 10 | 40 | 60 |


### **a. Insertion Sort**

---

Every iteration involves:

1. **Finding the correct position** to insert the next element (a.k.a, key) by looking back through the sorted portion of the list, finding **the first element that is less than the key**.
2. **Shifting elements** in each move to make room for the key to be inserted.
3. **Inserting** the key immediately after the element found in step 1. If none found, insert at the beginning of the list.

Starting with the array `[30, 50, 70, 10, 40, 60]`:

Since there are no elements before `30` to compare with, the first element is considered sorted.

> **30** | 50 | 70 | 10 | 40 | 60

Note that the **bold** numbers represent the sorted portion of the list.

**Iteration 1**: `i = 1`, key = `50`.

The first number that is less than `50` is `30`, so `50` is inserted after `30` (i.e., the second position).

> **30** | **50** | 70 | 10 | 40 | 60

**Iteration 2**: `i = 2`, key = `70`.

The first number that is less than `70` is `50`, so `70` is inserted after `50` (i.e., the third position).

> **30** | **50** | **70** | 10 | 40 | 60

**Iteration 3**: `i = 3`, key = `10`.

Since no number in the sorted portion is less than `10`, `10` is inserted at the beginning of the list.

> **10** | **30** | **50** | **70** | 40 | 60

**Iteration 4**: `i = 4`, key = `40`.

The first number that is less than `40` is `30`, so `40` is inserted after `30` (i.e., the third position).

> **10** | **30** | **40** | **50** | **70** | 60

**Iteration 5**: `i = 5`, key = `60`.

The first number that is less than `60` is `50`, so `60` is inserted after `50` (i.e., the fifth position).

> **10** | **30** | **40** | **50** | **60** | **70**

### **b. Selection Sort**

---

Every iteration involves:

1. **Finding the next smallest element** in the unsorted portion of the list.
2. **Swapping** the next smallest element with the first element in the unsorted portion of the list.

Starting with the array `[30, 50, 70, 10, 40, 60]`:

> 30 | 50 | 70 | 10 | 40 | 60

**Iteration 1**: `i = 0`, needs to find the smallest element in the list.

The smallest element is `10` at index `j = 3`, so `10` is swapped with `30`.

> 30 | 50 | 70 | **10** | 40 | 60 - Select
> 
> **10** | 50 | 70 | **30** | 40 | 60 - Swap

**Iteration 2**: `i = 1`, needs to find the next (second) smallest element in the list.

The smallest element is `30` at index `j = 3`, so `30` is swapped with `50`.

> 10 | 50 | 70 | **30** | 40 | 60 - Select
>
> 10 | **30** | 70 | **50** | 40 | 60 - Swap

**Iteration 3**: `i = 2`, needs to find the next (third) smallest element in the list.

The smallest element is `40` at index `j = 4`, so `40` is swapped with `70`.

> 10 | 30 | 70 | **40** | 50 | 60 - Select
>
> 10 | 30 | **40** | **70** | 50 | 60 - Swap

**Iteration 4**: `i = 3`, needs to find the next (fourth) smallest element in the list.

The smallest element is `50` at index `j = 4`, so `50` is swapped with `70`.

> 10 | 30 | 40 | 70 | **50** | 60 - Select
>
> 10 | 30 | 40 | **50** | **70** | 60 - Swap

**Iteration 5**: `i = 4`, needs to find the next (fifth) smallest element in the list.

The smallest element is `60` at index `j = 5`, so `60` is swapped with `70`.

> 10 | 30 | 40 | 50 | 70 | **60** - Select
>
> 10 | 30 | 40 | 50 | **60** | **70** - Swap

No need to check `i = n - 1 = 5`, as there is only one element left, and it must be the `n-th` smallest element (and will be swapped with itself anyway).

### **c. Bubble Sort**

---

Every iteration involves **comparing adjacent elements** and **swapping** them if they are in the wrong order (i.e., the first element is larger than the second).

Starting with the array `[30, 50, 70, 10, 40, 60]`:

> 30 | 50 | 70 | 10 | 40 | 60

**Iteration 1**:

Note that *italic* numbers represent the elements being compared, and **bold** represents elements just swapped.

> *30* | *50* | 70 | 10 | 40 | 60 - 30 < 50, no swap
>
> 30 | *50* | *70* | 10 | 40 | 60 - 30 < 70, no swap
>
> 30 | 50 | *70* | *10* | 40 | 60 - 70 > 10, swap
>
> 30 | 50 | **10** | ***70*** | *40* | 60 - 70 > 40, swap
>
> 30 | 50 | 10 | **40** | ***70*** | *60* - 70 > 60, swap

Final state of the array after the first iteration:

> 30 | 50 | 10 | 40 | **60** | **70**

**Iteration 2**:

> *30* | *50* | 10 | 40 | 60 | 70 - 30 < 50, no swap
>
> 30 | *50* | *10* | 40 | 60 | 70 - 50 > 10, swap
>
> 30 | **10** | ***50*** | *40* | 60 | 70 - 50 > 40, swap
>
> 30 | 10 | **40** | ***50*** | *60* | 70 - 50 < 60, no swap

Final state of the array after the second iteration:

> 30 | 10 | 40 | 50 | 60 | 70

Note that we are doing one less comparison, as we know that the last two elements are already in their correct positions.

**Iteration 3**:

> *30* | *10* | 40 | 50 | 60 | 70 - 30 > 10, swap
>
> **10** | ***30*** | *40* | 50 | 60 | 70 - 30 < 40, no swap
>
> 10 | 30 | *40* | *50* | 60 | 70 - 40 < 50, no swap

Final state of the array after the third iteration:

> 10 | 30 | 40 | 50 | 60 | 70

Again, since the last three elements are already in their correct positions, we can stop the iteration one step earlier.

**Iteration 4**:

> *10* | *30* | 40 | 50 | 60 | 70 - 10 < 30, no swap
>
> 10 | *30* | *40* | 50 | 60 | 70 - 30 < 40, no swap


Final state of the array after the fourth iteration:

> 10 | 30 | 40 | 50 | 60 | 70

In a more optimised version of the bubble sort, if no swaps are made in an iteration, we can stop the algorithm early. However, in this version, we move on.

**Iteration 5**:

> *10* | *30* | 40 | 50 | 60 | 70 - 10 < 30, no swap

Final state of the array after the fifth iteration:

> 10 | 30 | 40 | 50 | 60 | 70

# Part B: Programming Tasks

---

## **Question 4**: Implementing Insertion Sort

Recall the Insertion Sort algorithm below:

```pseudocode
ALGORITHM InsertionSort(A[0..n-1])
// Sorts a given array by insertion sort
// Input: An array A[0..n-1] of n orderable elements
// Output: Array A[0..n-1] sorted in nondecreasing order
for j <- 1 to n-1 do
    key <- A[j]
    i <- j - 1
    while i >= 0 and A[i] > key do
        A[i+1] <- A[i]
        i <- i - 1
    A[i+1] <- key
```

a. **Implement** the Insertion Sort algorithm using C#. The signature of this method should resemble:

```csharp
void InsertionSort(int A[], int n);
```

> **Answer**: This is a rather straightforward case of translating the pseudocode into C# code. Here is an implementation of the Insertion Sort algorithm in C#:

```csharp
using System;

namespace InsertionSort
{
    class Program
    {
        static void InsertionSort(int[] A, int n)
        {
            for (int i = 1; i <= n - 1; i++)
            {
                int v = A[i];
                int j = i - 1;
                while (j >= 0 && A[j] > v)
                {
                    A[j + 1] = A[j];
                    j = j - 1;
                }
                A[j + 1] = v;
            }
        }

        static void Main()
        {
            int[] arr = { 30, 50, 70, 10, 40, 60 };
            InsertionSort(arr, arr.Length);

            foreach (int num in arr)
            {
                Console.Write(num + " ");
            }
        }
    }
}
```

b. **Verify that your implementation is correct.** You could do this programmatically or manually, for example, by printing the contents of the array before and after calling the sort function and inspecting the output. Consider more than one case here. Does your implementation behave correctly on an already-sorted array, as well as unsorted
arrays?

> **Answer**: To verify, include the following test cases
>
> 1. An unsorted array: `[30, 50, 70, 10, 40, 60]`
> 2. A sorted array: `[10, 30, 40, 50, 60, 70]`
> 3. A reverse-sorted array: `[70, 60, 50, 40, 30, 10]`
> 4. An array with zero elements: `[]`
> 5. An array with one element: `[42]`
> 6. An array with all repeated elements: `[10, 10, 10, 10, 10]`
> 7. An array with some repeated elements: `[7, 7, 3, 1, 8, 1, 9, 4, 1, 10, 7]`

```csharp
static void Main()
{
    int[][] testCases = {
        new int[] { 30, 50, 70, 10, 40, 60 },
        new int[] { 10, 30, 40, 50, 60, 70 },
        new int[] { 70, 60, 50, 40, 30, 10 },
        new int[] { },
        new int[] { 42 },
        new int[] { 10, 10, 10, 10, 10 },
        new int[] { 7, 7, 3, 1, 8, 1, 9, 4, 1, 10, 7 }
    };

    string[] testNames = {
        "Unsorted array",
        "Sorted array",
        "Reverse-sorted array",
        "Array with zero elements",
        "Array with one element",
        "Array with repeated elements",
        "Array with some repeated elements"
    };

    for (int i = 0; i < testCases.Length; i++)
    {
        int[] arr = testCases[i];
        Console.WriteLine($"Running test case: {testNames[i]}");
        Console.WriteLine($"Before sorting: {string.Join(", ", arr)}");
        InsertionSort(arr, arr.Length);
        Console.WriteLine($"After sorting: {string.Join(", ", arr)}");
        Console.WriteLine();
    }
}
```

The output should look like:

```plaintext
Running test case: Unsorted array
Before sorting: 30, 50, 70, 10, 40, 60
After sorting: 10, 30, 40, 50, 60, 70

Running test case: Sorted array
Before sorting: 10, 30, 40, 50, 60, 70
After sorting: 10, 30, 40, 50, 60, 70

Running test case: Reverse-sorted array
Before sorting: 70, 60, 50, 40, 30, 10
After sorting: 10, 30, 40, 50, 60, 70

Running test case: Array with zero elements
Before sorting:
After sorting:

Running test case: Array with one element
Before sorting: 42
After sorting: 42

Running test case: Array with repeated elements
Before sorting: 10, 10, 10, 10, 10
After sorting: 10, 10, 10, 10, 10

Running test case: Array with some repeated elements
Before sorting: 7, 7, 3, 1, 8, 1, 9, 4, 1, 10, 7
After sorting: 1, 1, 1, 3, 4, 7, 7, 7, 8, 9, 10
```

---

## **Question 5**: Customer Collection (with Sorting)

This is an application of the sorting algorithms introduced in Lecture 4. In last workshop, you created a reusable class, namely `CustomerCollection`, as a data structure to store a collection of `Customer` objects. In the `CustomerCollection` class, you used an array of `Customer` objects as its underlying data structure to store those `Customer` objects, and designed and implemented a list of class methods (operations), including:
- **Find** – Given the **first name** and **last name** of a customer, this method **finds** the contact **phone number** of the customer from the data structure.
- **Insert** – Given the **first name**, **last name** and contact **phone number** of a customer, this method **inserts** this customer into the data structure.
- **Insert** – This method **inserts** an object of Customer class into the data structure.
- **Delete** – Given the **first name** and **last name** of a customer, this method removes the customer out of the data structure.
- **Display** – This method displays the information about all the customers in the data structure.

In this application, you add the following new class method (operation) into the
`CustomerCollection` class:

- **Sort** – This method reorganises the customers in the data structure in **alphabetical order** of their full names. 

Then, you write an application program to test this new class method (operation),
following the following procedure:
- Create an object of the `CustomerCollection` class as a data structure to store a
collection of customers’ information
- Use the `Insert` method to insert some customers into the data structure
- Use the `Display` method to display the information about all the customers in the
data structure
- Use the `Sort` method to reorganise the customers in the `CustomerCollection` object
- Use the `Display` method to confirm the customers have been reorganised in
alphabetical order by their full names.

We are going to reuse the `Customer` and `CustomerCollection` classes from the previous workshop. The `Customer` class is defined as follows:

```csharp
using System;

namespace CustomerCollection
{
    internal class Customer
    {
        public string FirstName { get; private set; }
        public string LastName { get; private set; }
        public string PhoneNumber { get; private set; }
        public Customer(string firstName, string lastName, string phoneNumber)
        {
            FirstName = firstName;
            LastName = lastName;
            PhoneNumber = phoneNumber;
        }
        public override string ToString()
        {
            return $"{FirstName} {LastName}, {PhoneNumber}";
        }
    }
}
```

The `CustomerCollection` class is defined as follows:

```csharp
using System;

namespace CustomerCollection
{
    internal class CustomerCollection
    {
        public int Capacity { get; private set; }
        public int Count { get; private set; }

        private Customer[] data;

        public CustomerCollection(int capacity = 10)
        {
            Capacity = capacity;
            Count = 0;
            data = new Customer[Capacity];
        }

        public void Clear()
        {
            Count = 0;
            data = new Customer[Capacity];
        }

        public void Insert(string firstName, string lastName, string phoneNumber)
        {
            Customer newCustomer = new Customer(firstName, lastName, phoneNumber);
            Insert(newCustomer);
        }

        public void Insert(Customer customer)
        {
            if (IsFull()) return;
            data[Count] = customer;
            Count++;
        }

        public string Find(string firstName, string lastName)
        {
            for (int i = 0; i < Count; i++)
            {
                Customer current = data[i];
                if (current.FirstName.Equals(firstName)
                    && current.LastName.Equals(lastName))
                {
                    return current.PhoneNumber;
                }
            }
            return null;
        }

        public void Delete(string firstName, string lastName)
        {
            if (Find(firstName, lastName) == null) return;
            // Find the index to delete
            int index;
            for (index = 0; index < Count; index++)
            {
                Customer current = data[index];
                if (current.FirstName.Equals(firstName)
                    && current.LastName.Equals(lastName))
                {
                    break;
                }
            }
            // Shift everything after that index to the left
            for (; index < Count - 1; index++)
            {
                data[index] = data[index + 1];
            }
            Count--;
        }

        public bool IsFull()
        {
            return Count == Capacity;
        }

        public void Display()
        {
            foreach (Customer customer in data)
            {
                if (customer == null) continue;
                Console.WriteLine(customer);
            }
        }
    }
}
```

Before implementing the `Sort` method, we will need a way to compare the `Customer` objects based on their full names. We can achieve this by adding an `int CompareTo(Customer other)` method to the `Customer` class. This method will compare two `Customer` objects based on their full names.

The `CompareTo` method should return a negative integer (`-1`) if the current `Customer` object should come before the `other` object, a positive integer (`1`) if the current `Customer` object should come after the `other` object, and `0` if they are equal. This means `A[i] < A[j]` is equivalent to `A[i].CompareTo(A[j]) < 0`.

```csharp
public int CompareTo(Customer other)
{
    // Try to compare first names first
    if (!FirstName.Equals(other.FirstName))
    {
        return string.Compare(FirstName, other.FirstName);
    }
    // Only need to compare last names if first names are equal
    return string.Compare(LastName, other.LastName);
}
```

Note that in the above, instead of calculating a `fullName` string, we are saving on memory by comparing the first names first. If the first names are equal, we then compare the last names.

Now, let's add the `Sort` method to the `CustomerCollection` class, implementing one of the sorting algorithms above, using `data` in place of an array `A`, and `Count` in place of `n`.

Feel free to pick any sorting algorithm you like from below:

**Insertion Sort**:
```csharp
public void Sort()
{
    for (int i = 1; i <= Count - 1; i++)
    {
        Customer v = data[i];
        int j = i - 1;
        while (j >= 0 && data[j].CompareTo(v) > 0)
        {
            data[j + 1] = data[j];
            j = j - 1;
        }
        data[j + 1] = v;
    }
}
```

**Selection Sort**:
```csharp
public void Sort()
{
    for (int i = 0; i <= Count - 2; i++)
    {
        int min = i;
        for (int j = i + 1; j <= Count - 1; j++)
        {
            if (data[j].CompareTo(data[min]) < 0) min = j;
        }
        Swap(i, min);
    }
}

// Helper method to swap two elements in the data array
public void Swap(int i, int j)
{
    Customer temp = data[i];
    data[i] = data[j];
    data[j] = temp;
}
```

**Bubble Sort**:
```csharp
public void Sort()
{
    for (int i = 0; i <= Count - 2; i++)
    {
        for (int j = 0; j <= Count - 2 - i; j++)
        {
            if (data[j + 1].CompareTo(data[j]) < 0)
            {
                Swap(j, j + 1);
            }
        }
    }
}
```

Now, let's create a test program to verify the `Sort` method:

```csharp
using System;

namespace CustomerCollection
{
    class Program
    {
        static void Main(string[] args)
        {
            CustomerCollection customers = new CustomerCollection(10);

            customers.Insert("John", "Doe", "1234567890");
            customers.Insert("Jane", "Smith", "0987654321");
            customers.Insert("Alice", "Johnson", "1112223333");
            customers.Insert("Bob", "Brown", "4445556666");

            Console.WriteLine("Before sorting:");
            customers.Display();

            customers.Sort();

            Console.WriteLine("\nAfter sorting:");
            customers.Display();
        }
    }
}
```

Run the program to see the customers sorted by their full names:

```plaintext
Before sorting:
John Doe, 1234567890
Jane Smith, 0987654321
Alice Johnson, 1112223333
Bob Brown, 4445556666

After sorting:
Alice Johnson, 1112223333
Bob Brown, 4445556666
Jane Smith, 0987654321
John Doe, 1234567890
```
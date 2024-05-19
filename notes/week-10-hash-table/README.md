---
layout: default
title: Workshop 10 - Hash Tables
nav_order: 8
has_children: false
permalink: /workshop-10
---

# Workshop 10: Hash Tables

## Part A: Tutorial Questions

### Question 1: Division Method

A hash function is a formula that maps key values into the addresses of an array in which the key-and-value pairs are stored. Using the Division method of hashing $h(k) = k \pmod M$ given the following information show the resulting hash table:

```plaintext
K = [ 2341, 4234, 2839, 352, 22, 397, 3920 ]
```

Hash table size = 7
Hash function $h(k) = k \pmod 7$

## Question 2. Middle Square Method

Using the Middle Square method the key is squared – use the middle 3 bits as the index into the hash table for the following values. Assume the hash table has an index ranging from 0 to 999.

```plaintext
K = [ 1221, 2134, 2254, 2452, 2941, 1000, 1874 ]
```

## Question 3. Folding Method

Apply the folding method of hashing to the following keys. Assume we have a hash table ranging from index 0 to 999.

```plaintext
K = [ 189554134678,98214587412,567154662,1546591,65378456,982154 ]
```

a. Based on the size of the hash table, how many digits should be grouped to determine the index at which the key belongs?

b. Calculate the address of the keys using shift folding.

c. Apply folding at the boundaries to the above keys to calculate the address of the keys.

d. Apply the selecting digits method by extracting the 6th, 4th, and 1st value from the keys to calculate the relative address.

## Question 4. Linear Probing

A hash table uses linear probing to resolve collisions. The size of the hash table is 7 and the hash function is. Initially, the hash table is empty.

```
a. Simulate the behaviour of the hash table when the following actions are
performed:
```
```
i. Insert 374, 1091, 911, 227, 421, 161, 83;
ii. Lookup 1091, 83, 1092;
iii. Delete 911;
iv. Lookup 83.
```
```
b. Find
i. The load factor;
ii. The average number of probes to find a value that is in the table;
iii. The average number of probes to find that a value is not in the table.
```
```
c. Repeat part (a) for a hash table that uses separate chaining to resolve
collisions.
```
## Question 5. Hash table structures

Assume you have a hash table which will store integers with 11 buckets.The hash function to be used to decide on the index will be:

$$
h(k) = k \pmod{NUM\_BUCKETS}
$$

Draw up the structure of the hash table after inserting the following values:

38, 31, 29, 50, 42, 12, 17, 23, 16, 55

a. Open addressing using linear probing

b. Open addressing using quadratic probing

c. Separate chaining

# Part B: Programming Questions

## Question 6. Hash Table implementation

Below is the specification of a hash table ADT (Abstract Data Type). 

```csharp
interface IHashtable
{
    int Count //get the number of elements in the hash table
    {
        get;
    }
    int Capacity //get and set of the capacity of the hash table
    {
        get;
        set;
    }
    /* pre: true
    * post: return the bucket where the key is stored
    * if the given key in the hash table;
    * otherwise, return -1.
    */
    int Search(int key);
    /* pre: true
    * post: all the elements in the hash table have been removed
    */
    void Clear();
    /* pre: true
    * post: the given key has been inserted into the hash table
    */
    void Insert(int key);
    /* pre: nil
    * post: the given key has been removed from the hash table
    *if the given key is in the hash table
    */
    void Delete(int key); //delete the key from the hash table
    /* pre: nil
    * post: print all the elements in the hash table
    */
    void Print();
}
```

Implement the hash table ADT and test it using the following data:

a. Create a hash table of capacity of 17

b. Add the following elements one by one in the order into the hash table:

c. Delete the following elements one by one in the order from the hash table

d. Show the status of the hash table after each addition and deletion
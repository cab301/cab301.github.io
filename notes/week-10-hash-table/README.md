---
layout: default
title: Workshop 10 - Hash Tables
nav_order: 8
has_children: false
permalink: /workshop-10
math: mathjax3
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

{: .note-title }
> **Answer**
>
> For each key, calculate $h(k)$ and place the key in the corresponding index of the hash table.
>
> $$
> \begin{align*}
> h(2341) = 2341 \pmod 7 &= 3 \\
> h(4234) = 4234 \pmod 7 &= 6 \\
> h(2839) = 2839 \pmod 7 &= 4 \\
> h(352) = 352 \pmod 7 &= 2 \\
> h(22) = 22 \pmod 7 &= 1 \\
> h(397) = 397 \pmod 7 &= 5 \\
> h(3920) = 3920 \pmod 7 &= 0 \\
> \end{align*}
> $$
>
> Rearrange by index:
>
> $$
> \begin{align*}
> h(3920) = 3920 \pmod 7 &= 0 \\
> h(22) = 22 \pmod 7 &= 1 \\
> h(352) = 352 \pmod 7 &= 2 \\
> h(2341) = 2341 \pmod 7 &= 3 \\
> h(2839) = 2839 \pmod 7 &= 4 \\
> h(397) = 397 \pmod 7 &= 5 \\
> h(4234) = 4234 \pmod 7 &= 6 \\
> \end{align*}
> $$
>
> And the resulting hash table is:
>
> | Index | Key |
> |-------|-----|
> | 0     | 3920 |
> | 1     | 22 |
> | 2     | 352 |
> | 3     | 2341 |
> | 4     | 2839 |
> | 5     | 397 |
> | 6     | 4234 |

## Question 2. Middle Square Method

Using the Middle Square method the key is squared – use the middle 3 bits as the index into the hash table for the following values. Assume the hash table has an index ranging from 0 to 999.

```plaintext
K = [ 1221, 2134, 2254, 2452, 2941, 1000, 1874 ]
```

{: .note-title }
> **Answer**
>
> For each key, calculate the middle square and extract the middle 3 bits to determine the index.
>
> $$
> \begin{align*}
> 1221^2 &= 14\textbf{908}41 \\
> 2134^2 &= 45\textbf{539}56 \\
> 2254^2 &= 50\textbf{805}16 \\
> 2452^2 &= 60\textbf{123}04 \\
> 2941^2 &= 86\textbf{494}81 \\
> 1000^2 &= 10\textbf{000}00 \\
> 1874^2 &= 35\textbf{118}76 \\
> \end{align*}
> $$
> 
> Extract the middle 3 bits:
>
> $$
> \begin{align*}
> h(1221) &= 908 \\
> h(2134) &= 539 \\
> h(2254) &= 805 \\
> h(2452) &= 123 \\
> h(2941) &= 494 \\
> h(1000) &= 000 \\
> h(1874) &= 118 \\
> \end{align*}
> $$
>
> And the resulting hash table is:
>
> | Index | Key |
> |-------|-----|
> | 908   | 1221 |
> | 539   | 2134 |
> | 805   | 2254 |
> | 123   | 2452 |
> | 494   | 2941 |
> | 0   | 1000 |
> | 118   | 1874 |

## Question 3. Folding Method

Apply the **folding method** of hashing to the following keys. Assume we have a hash table ranging from index 0 to 999.

```plaintext
K = [ 189554134678,98214587412,567154662,1546591,65378456,982154 ]
```

a. Based on the size of the hash table, how many digits should be grouped to determine the index at which the key belongs?

{: .note-title }
> **Answer**
>
> Since the index ranges from 000 to 999 (3 digits), we should group the keys into 3 digits.

b. Calculate the address of the keys using **shift folding**.

{: .note-title }
> **Answer**
>
> For each key, group the digits into 3 and sum them up.
>
> $$
> \begin{align*}
> 189~554~134~678 &\rightarrow 189 + 554 + 134 + 678 &= 1\textbf{555} \\
> 982~145~874~12 &\rightarrow 982 + 145 + 874 + 12 &= 2\textbf{013} \\
> 567~154~662 &\rightarrow 567 + 154 + 662 &= 1\textbf{383} \\
> 154~659~1 &\rightarrow 154 + 659 + 1 &= ~~\textbf{814} \\
> 653~784~56 &\rightarrow 653 + 784 + 56 &= 1\textbf{493} \\
> 982~154 &\rightarrow 982 + 154 &= 1\textbf{136} \\
> \end{align*}
> $$
>
> If the sum is greater than 999, we ignore the first digit.
>
> So the resulting hash table is:
>
> | Index | Key |
> |-------|-----|
> | 555   | 189554134678 |
> | 13    | 98214587412 |
> | 383   | 567154662 |
> | 814   | 1546591 |
> | 493   | 65378456 |
> | 136   | 982154 |

c. Apply **folding at the boundaries** to the above keys to calculate the address of the keys.

{: .note-title }
> **Answer**
>
> Similar to the above, split the keys into groups of 3. However, we reverse every other group (starting from the second group from the right) before summing them up.
>
> $$
> \begin{align*}
> 189~554~134~678 &\rightarrow 189 + 455 + 134 + 876 &= 1\textbf{654} \\
> 982~145~874~12 &\rightarrow 982 + 541 + 874 + 21 &= 2\textbf{418} \\
> 567~154~662 &\rightarrow 567 + 451 + 662 &= 1\textbf{680} \\
> 154~659~1 &\rightarrow 154 + 956 + 1 &= 1\textbf{111} \\
> 653~784~56 &\rightarrow 653 + 487 + 56 &= 1\textbf{196} \\
> 982~154 &\rightarrow 982 + 451 &= 1\textbf{433} \\
> \end{align*}
> $$
>
> And the resulting hash table is:
>
> | Index | Key |
> |-------|-----|
> | 654   | 189554134678 |
> | 418   | 98214587412 |
> | 680   | 567154662 |
> | 111   | 1546591 |
> | 196   | 65378456 |
> | 433   | 982154 |

d. Apply the **selecting digits** method by extracting the **6th, 4th, and 1st** value from the keys to calculate the relative address.

{: .note-title }
> **Answer**
>
> For each key, extract the 6th, 4th, and 1st digits (from the right) and concatenate them to form the index.
>
> | Key | 6th | 4th | 1st | Index |
> |-----|-----|-----|-----|-------|
> | `1`89`5`5`4`134678 | 4 | 5 | 1 | 451 |
> | `9`82`1`4`5`87412 | 5 | 1 | 9 | 519 |
> | `5`67`1`5`4`662 | 4 | 1 | 5 | 415 |
> | `1`54`6`5`9`1 | 9 | 6 | 1 | 961 |
> | `6`53`7`8`4`56 | 4 | 7 | 6 | 476 |
> | `9`82`1`5`4` | 4 | 1 | 9 | 419 |

## Question 4. Linear Probing

A hash table uses linear probing to resolve collisions. The size of the hash table is 7 and the hash function is $h(k) = k \pmod 7$. Initially, the hash table is empty.

**a. Simulate the behaviour of the hash table when the following actions are
performed:**

**i. Insert 374, 1091, 911, 227, 421, 161, 83;**

{: .note-title }
> **Answer**
>
> For each key, calculate $h(k)$ and place the key in the corresponding index of the hash table. 
> 
> If the index is already occupied, probe linearly until an empty slot is found.
> 
> $$
> \begin{align*}
> h(374) &= 374 \pmod 7 &= 3 \\
> \end{align*}
> $$
>
> So far, the hash table is:
>
> | Index | Key |
> |-------|-----|
> | 0     |     |
> | 1     |     |
> | 2     |     |
> | 3     | 374 |
> | 4     |     |
> | 5     |     |
> | 6     |     |
>
> Similarly:
>
> $$
> \begin{align*}
> h(1091) &= 1091 \pmod 7 &= 6 \\
> h(911) &= 911 \pmod 7 &= 1
> \end{align*}
> $$
>
> The hash table is now:
>
> | Index | Key |
> |-------|-----|
> | 0     |     |
> | 1     | 911 |
> | 2     |     |
> | 3     | 374 |
> | 4     |     |
> | 5     |     |
> | 6     | 1091 |
>
> For 227, we get a collision at index 3:
>
> $$
> \begin{align*}
> h(227) &= 227 \pmod 7 &= 3 
> \end{align*}
> $$
>
> We try the next index, 4, which is empty, so we place 227 there.
>
> | Index | Key |
> |-------|-----|
> | 0     |     |
> | 1     | 911 |
> | 2     |     |
> | 3     | 374 |
> | 4     | 227 |
> | 5     |     |
> | 6     | 1091 |
>
> Similarly:
>
> - 421: $h(421) = 421 \pmod 7 = 1$ collision at index 1. Next index is 2, which is empty, so we place 421 there.
> - 161: $h(161) = 161 \pmod 7 = 0$, which is empty, so we place 161 there.
>
> | Index | Key |
> |-------|-----|
> | 0     | 161 |
> | 1     | 911 |
> | 2     | 421 |
> | 3     | 374 |
> | 4     | 227 |
> | 5     |     |
> | 6     | 1091 |
>
> Finally, 83: $h(83) = 83 \pmod 7 = 6$, which is already occupied. So we probe linearly:
>
> - Nothing after 6, so wrap around to 0. 0 is occupied, so we move to 1.
> - 1 is occupied, so we move to 2.
> - 2 is occupied, so we move to 3.
> - 3 is occupied, so we move to 4.
> - 4 is occupied, so we move to 5.
> - 5 is empty, so we place 83 there.
>
> The final hash table is:
>
> | Index | Key |
> |-------|-----|
> | 0     | 161 |
> | 1     | 911 |
> | 2     | 421 |
> | 3     | 374 |
> | 4     | 227 |
> | 5     | 83 |
> | 6     | 1091 |

**ii. Lookup 1091, 83, 1092;**

{: .note-title }
> **Answer**
>
> To lookup a key, calculate $h(k)$ and check if the key is in the corresponding index. If not, probe linearly until the key is found or an empty slot is reached.
>
> $$
> \begin{align*}
> h(1091) &= 1091 \pmod 7 &= 6 \\
> h(83) &= 83 \pmod 7 &= 6 \\
> h(1092) &= 1092 \pmod 7 &= 0 \\
> \end{align*}
> $$
>
> For 1091, we find it immediate at index 6.
>
> For 83, we start at index 6, and probe linearly:
>
> - Key at 6 is 1091 (not 83), so we move to 0.
> - Key at 0 is 161 (not 83), so we move to 1.
> - Key at 1 is 911 (not 83), so we move to 2.
> - Key at 2 is 421 (not 83), so we move to 3.
> - Key at 3 is 374 (not 83), so we move to 4.
> - Key at 4 is 227 (not 83), so we move to 5.
> - Key at 5 is 83, so we found it.
>
> For 1092, we start at index 0, and probe linearly:
>
> - Key at 0 is 161 (not 1092), so we move to 1.
> - Key at 1 is 911 (not 1092), so we move to 2.
> - Key at 2 is 421 (not 1092), so we move to 3.
> - Key at 3 is 374 (not 1092), so we move to 4.
> - Key at 4 is 227 (not 1092), so we move to 5.
> - Key at 5 is 83 (not 1092), so we move to 6.
> - Key at 6 is 1091 (not 1092), so we wrap around to 0. Since we have already visited 0, we stop and conclude that 1092 is not in the hash table.

**iii. Delete 911;**

{: .note-title }
> **Answer**
>
> To delete a key, calculate $h(k)$ and check if the key is in the corresponding index. If not, probe linearly until the key is found or an empty slot is reached.
>
> $$
> \begin{align*}
> h(911) &= 911 \pmod 7 &= 1 \\
> \end{align*}
> $$
>
> We find 911 at index 1. To delete it, we mark the index as empty, or set it to a certain value to indicate that it is deleted, like "DEL":
>
> | Index | Key |
> |-------|-----|
> | 0     | 161 |
> | 1     | DEL |
> | 2     | 421 |
> | 3     | 374 |
> | 4     | 227 |
> | 5     | 83 |
> | 6     | 1091 |

**iv. Lookup 83.**

{: .note-title }
> **Answer**
>
> Similar to the lookup of 83 in part (ii), we calculate $h(83)$ and probe linearly until we find the key.
>
> $$
> \begin{align*}
> h(83) &= 83 \pmod 7 &= 6 \\
> \end{align*}
> $$
>
> Probing linearly:
>
> - Key at 6 is 1091 (not 83), so we move to 0.
> - Key at 0 is 161 (not 83), so we move to 1.
> - Key at 1 is DEL, so we move to 2.
> - Key at 2 is 421 (not 83), so we move to 3.
> - Key at 3 is 374 (not 83), so we move to 4.
> - Key at 4 is 227 (not 83), so we move to 5.
> - Key at 5 is 83, so we found it.

**b. Find**

**i. The load factor;**

{: .note-title }
> **Answer**
>
> The load factor is the ratio of the number of keys in the hash table to the size of the hash table.
>
> $$
> \text{L} = \frac{\text{Number of keys}}{\text{Size of hash table}} = \frac{6}{7} \approx 0.857
> $$

**ii. The average number of probes to find a value that is in the table;**

{: .note-title }
> **Answer**
>
> To find the average number of probes to find a value that is in the table, we sum the number of probes for each key and divide by the number of keys.
>
> | Key | Hash | Sequence | Number of Probes |
> |-----|------|----------|------------------|
> | 161 | 0    | 0        | 1                |
> | 421 | 1    | 1, 2     | 2                |
> | 374 | 3    | 3        | 1                | 
> | 227 | 3    | 3, 4       | 2                |
> | 83  | 6    | 6, 0, 1, 2, 3, 4, 5        | 7                |
> | 1091| 6    | 6        | 1                |
>
> The total number of probes is 1 + 2 + 1 + 2 + 7 + 1 = 14. The average number of probes is $\frac{14}{6} \approx 2.33$.

**iii. The average number of probes to find that a value is not in the table.**

**c. Repeat part (a) for a hash table that uses separate chaining to resolve
collisions.**

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
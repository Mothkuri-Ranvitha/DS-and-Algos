# Variation 2: Range Sum Query

## LeetCode

**LC303 - Range Sum Query - Immutable**

Difficulty: Easy

---

## Problem Statement

Given an integer array `nums`, handle multiple queries of the following type:

```text
Calculate the sum of elements between
left and right inclusive.
```

Implement:

```text
sumRange(left, right)
```

Example:

```text
Input:

nums = [-2,0,3,-5,2,-1]

sumRange(0,2)

Output:

1
```

Because:

```text
-2 + 0 + 3 = 1
```

---

## Why Does This Problem Exist?

LC1480 taught us:

```text
How to build Prefix Sum.
```

LC303 teaches:

```text
How to USE Prefix Sum.
```

This is the first problem where Prefix Sum becomes powerful.

---

## Brute Force Thinking

Suppose:

```text
nums

[2,3,1,5,4]
```

Query:

```text
sumRange(1,3)
```

We calculate:

```text
3+1+5
```

Now imagine:

```text
10000 queries
```

Every query loops again.

Lots of repeated work.

---

## Core Observation

When building Prefix Sum:

```text
Array

[2,3,1,5,4]

Prefix

[2,5,6,11,15]
```

Notice:

```text
Prefix[3]

=

2+3+1+5
```

But we only want:

```text
3+1+5
```

Remove unwanted part:

```text
Prefix[0]

=

2
```

Therefore:

```text
11 - 2 = 9
```

Answer found instantly.

---

## Intuition

Think of Prefix Sum as:

```text
Total money earned till today.
```

If you want:

```text
Money earned between Day 5 and Day 10
```

You can do:

```text
Total till Day10

-

Total till Day4
```

Exactly the same idea.

---

## Visual Understanding

```text
Array

[2] [3] [1] [5] [4]

Index

 0   1   2   3   4
```

Prefix:

```text
[2] [5] [6] [11] [15]
```

Need:

```text
Sum(1,3)
```

Visual:

```text
Prefix[3]

2 + 3 + 1 + 5

Minus

Prefix[0]

2

Remaining

3 + 1 + 5
```

Answer:

```text
9
```

---

## Recognition Signal

Think Prefix Sum immediately when you see:

* Range Sum
* Multiple Queries
* Sum from L to R
* Immutable Array
* Repeated Calculations

Keywords:

```text
sumRange

range query

many queries

L to R sum
```

---

## Core Formula

When:

```text
L > 0
```

Formula:

```text
sum(L,R)

=

prefix[R]

-

prefix[L-1]
```

Special Case:

```text
L == 0
```

Then:

```text
sum(0,R)

=

prefix[R]
```

---

## Mental Model

```text
Want Middle Part

↓

Take Whole Prefix

↓

Remove Left Portion

↓

Answer Found
```

---

## How To Solve

### Step 1

Build Prefix Array

```text
prefix[i]

=

prefix[i-1]+nums[i]
```

---

### Step 2

Answer Query

```text
prefix[right]

-

prefix[left-1]
```

---

### Step 3

Return Answer

No loop required.

---

## Code

```java
class NumArray {

    int[] prefix;

    public NumArray(int[] nums) {

        prefix = new int[nums.length];

        prefix[0] = nums[0];

        for(int i = 1; i < nums.length; i++) {
            prefix[i] = prefix[i - 1] + nums[i];
        }
    }

    public int sumRange(int left, int right) {

        if(left == 0)
            return prefix[right];

        return prefix[right] - prefix[left - 1];
    }
}
```

---

## Dry Run

Input:

```text
[2,3,1,5,4]
```

Prefix:

```text
[2,5,6,11,15]
```

Query:

```text
sumRange(1,3)
```

Calculation:

```text
prefix[3]

-

prefix[0]

=

11-2

=

9
```

Answer:

```text
9
```

---

## Time Complexity

### Constructor

Building Prefix:

```text
O(N)
```

---

### Each Query

```text
O(1)
```

Only one subtraction.

---

## Space Complexity

```text
O(N)
```

For Prefix Array.

---

## Why Is This Better?

Without Prefix Sum:

```text
Each Query

O(N)
```

For 10000 queries:

```text
O(10000 × N)
```

With Prefix Sum:

```text
Build Once

O(N)

Every Query

O(1)
```

Huge improvement.

---

## Common Mistakes

### Mistake 1

Forgetting:

```text
left == 0
```

Special handling required.

---

### Mistake 2

Using:

```text
prefix[right]-prefix[left]
```

Wrong.

Correct:

```text
prefix[right]-prefix[left-1]
```

---

### Mistake 3

Not understanding why subtraction works.

Always visualize:

```text
Whole Prefix

-

Unwanted Prefix

=

Required Range
```

---

## Interview Explanation

"I noticed multiple range-sum queries on an immutable array. Recomputing sums for every query would be expensive. I built a Prefix Sum array where each index stores cumulative sum till that position. Then each query can be answered in O(1) using prefix[right] - prefix[left-1]."

---

## Key Insight

```text
Need a middle segment?

Take the whole prefix.

Remove the unwanted left part.
```

---

## Connection To Next Variation

LC1480 taught:

```text
How to build Prefix Sum.
```

LC303 teaches:

```text
How to query Prefix Sum.
```

Next:

```text
LC724 Pivot Index
```

will teach:

```text
How to compare Left Sum and Right Sum
using Prefix Sum.
```

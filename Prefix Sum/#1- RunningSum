# Variation 1: Running Sum

## LeetCode

**LC1480 - Running Sum of 1D Array**

Difficulty: Easy

---

## Problem Statement

Given an array `nums`, return the running sum of `nums`.

A running sum array is defined as:

```text
runningSum[i] = nums[0] + nums[1] + ... + nums[i]
```

Example:

```text
Input:

[1,2,3,4]

Output:

[1,3,6,10]
```

---

## Why Does This Problem Exist?

This is the first and simplest Prefix Sum problem.

The goal is not the answer itself.

The goal is to learn:

```text
How to build cumulative information.
```

Every advanced Prefix Sum problem depends on this idea.

---

## Intuition

Suppose we have:

```text
[1,2,3,4]
```

To calculate position 3:

```text
1+2+3+4
```

But we already know:

```text
1+2+3 = 6
```

Why calculate it again?

Instead:

```text
6 + 4 = 10
```

Reuse previous work.

This is the entire Prefix Sum philosophy.

```text
Previous Sum
+
Current Element
=
Current Running Sum
```

---

## Visual Understanding

```text
nums

[1] [2] [3] [4]

prefix

[1]
```

Step 1

```text
prefix[0]=1
```

---

Step 2

```text
prefix[1]

=
prefix[0]+nums[1]

=
1+2

=
3
```

```text
[1,3]
```

---

Step 3

```text
prefix[2]

=
3+3

=
6
```

```text
[1,3,6]
```

---

Step 4

```text
prefix[3]

=
6+4

=
10
```

```text
[1,3,6,10]
```

---

## Recognition Signal

Think Running Sum when you see:

* Running Total
* Cumulative Score
* Prefix Information
* Running Balance
* Total Till Current Position

Keywords:

```text
running sum

cumulative sum

total till now

prefix values
```

---

## Core Observation

Instead of recalculating:

```text
nums[0]+nums[1]+...+nums[i]
```

Use:

```text
prefix[i]

=

prefix[i-1]
+
nums[i]
```

This reduces repeated work.

---

## Formula

```text
prefix[i] = prefix[i-1] + nums[i]
```

Meaning:

```text
Current Prefix

=

Previous Prefix

+

Current Number
```

---

## Code

```java
class Solution {
    public int[] runningSum(int[] nums) {

        int[] prefix = new int[nums.length];

        prefix[0] = nums[0];

        for(int i = 1; i < nums.length; i++) {
            prefix[i] = prefix[i - 1] + nums[i];
        }

        return prefix;
    }
}
```

---

## Dry Run

Input:

```text
[5,1,7,2,4]
```

Initialization:

```text
prefix[0]=5
```

Current:

```text
[5]
```

---

i=1

```text
5+1=6
```

```text
[5,6]
```

---

i=2

```text
6+7=13
```

```text
[5,6,13]
```

---

i=3

```text
13+2=15
```

```text
[5,6,13,15]
```

---

i=4

```text
15+4=19
```

```text
[5,6,13,15,19]
```

Final Answer:

```text
[5,6,13,15,19]
```

---

## Time Complexity

Building prefix array:

```text
O(N)
```

because we traverse the array once.

---

## Space Complexity

```text
O(N)
```

because we create an additional prefix array.

---

## Can We Optimize?

Yes.

We can directly modify the input array.

Then:

```text
Space = O(1)
```

while keeping:

```text
Time = O(N)
```

---

## Interview Explanation

"I noticed each running sum contains the previous running sum plus the current element. Instead of recalculating sums repeatedly, I store cumulative information. Using Prefix Sum, each value can be built in O(1), giving an overall O(N) solution."

---

## Key Insight

```text
Don't recalculate what you already know.

Reuse previous work.
```

This single idea becomes:

```text
LC303 Range Sum Query

LC724 Pivot Index

LC560 Subarray Sum Equals K

LC930 Binary Subarrays With Sum
```

Everything in Prefix Sum starts here.

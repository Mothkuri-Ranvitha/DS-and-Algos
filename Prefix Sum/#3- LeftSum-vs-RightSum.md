# Variation 3: Left Sum vs Right Sum

## LeetCode

**LC724 - Find Pivot Index**

Difficulty: Easy

---

## Problem Statement

Given an integer array `nums`, find the pivot index.

A pivot index is an index where:

```text
Sum of all elements on left

=

Sum of all elements on right
```

If multiple pivot indices exist, return the leftmost one.

If none exist, return -1.

Example:

```text
Input:

[1,7,3,6,5,6]

Output:

3
```

Because:

```text
Left Sum

1+7+3 = 11

Right Sum

5+6 = 11
```

---

## Why Does This Problem Exist?

LC1480 taught:

```text
How to build Prefix Sum.
```

LC303 taught:

```text
How to answer range queries.
```

LC724 teaches:

```text
How to compare two regions efficiently.
```

This is the first problem where Prefix Sum is used for reasoning rather than direct queries.

---

## Brute Force Thinking

For every index:

Calculate:

```text
Left Sum
```

and

```text
Right Sum
```

separately.

Example:

```text
[1,7,3,6,5,6]
```

For index 3:

```text
Left

1+7+3
```

and

```text
Right

5+6
```

Works.

But notice:

```text
Lots of repeated calculations.
```

Every index recalculates the same sums.

---

## Core Observation

Suppose:

```text
Total Sum = 28
```

At index:

```text
i = 3

nums[i] = 6
```

If:

```text
Left Sum = 11
```

Then:

```text
Right Sum

=

Total Sum
-
Left Sum
-
Current Element
```

Because:

```text
Total

=

Left
+
Current
+
Right
```

Rearranging:

```text
Right

=

Total
-
Left
-
Current
```

Boom.

No need to calculate right side separately.

---

## Intuition

Imagine a balance scale.

```text
Left Side

?

Current Element

?

Right Side
```

Instead of calculating both sides repeatedly:

Calculate one side.

Use total sum to derive the other.

---

## Visual Understanding

Array:

```text
[1] [7] [3] [6] [5] [6]
```

Total:

```text
28
```

At index:

```text
6
```

Left Sum:

```text
1+7+3

=

11
```

Right Sum:

```text
28 - 11 - 6

=

11
```

Since:

```text
11 == 11
```

Pivot found.

---

## Recognition Signal

Think Pivot Logic when you see:

* Left side vs Right side
* Balance condition
* Equal sums
* Partition point
* Split array

Keywords:

```text
left sum

right sum

equilibrium

pivot

balance
```

---

## Mental Model

```text
Need Left Sum

↓

Get Total Sum

↓

Derive Right Sum

↓

Compare
```

---

## How To Solve

### Step 1

Find total sum.

```text
total = sum(nums)
```

---

### Step 2

Maintain:

```text
leftSum
```

Initially:

```text
0
```

---

### Step 3

For every index:

Compute:

```text
rightSum

=

total
-
leftSum
-
nums[i]
```

---

### Step 4

Check:

```text
leftSum == rightSum
```

If yes:

```text
Return i
```

---

### Step 5

Update:

```text
leftSum += nums[i]
```

Move ahead.

---

## Code

```java
class Solution {

    public int pivotIndex(int[] nums) {

        int total = 0;

        for(int num : nums) {
            total += num;
        }

        int leftSum = 0;

        for(int i = 0; i < nums.length; i++) {

            int rightSum =
                    total - leftSum - nums[i];

            if(leftSum == rightSum) {
                return i;
            }

            leftSum += nums[i];
        }

        return -1;
    }
}
```

---

## Dry Run

Input:

```text
[1,7,3,6,5,6]
```

Total:

```text
28
```

---

i = 0

```text
Left = 0

Right = 28-0-1

= 27
```

Not Equal

Update:

```text
Left = 1
```

---

i = 1

```text
Left = 1

Right = 28-1-7

= 20
```

Not Equal

Update:

```text
Left = 8
```

---

i = 2

```text
Left = 8

Right = 28-8-3

= 17
```

Not Equal

Update:

```text
Left = 11
```

---

i = 3

```text
Left = 11

Right = 28-11-6

= 11
```

Equal.

Return:

```text
3
```

---

## Time Complexity

### First Loop

```text
O(N)
```

Find total.

---

### Second Loop

```text
O(N)
```

Check pivot.

---

Overall:

```text
O(N)
```

---

## Space Complexity

```text
O(1)
```

Only variables used.

No extra array.

---

## Common Mistakes

### Mistake 1

Calculating right sum separately.

Unnecessary.

Use:

```text
total - leftSum - nums[i]
```

---

### Mistake 2

Updating leftSum before comparison.

Wrong order.

Always:

```text
Compare

↓

Update leftSum
```

---

### Mistake 3

Forgetting current element belongs to neither side.

Right Sum should be:

```text
total
-
leftSum
-
nums[i]
```

---

## Interview Explanation

"I observed that calculating left and right sums separately causes repeated work. Using the total sum of the array, I can derive the right sum from the left sum. For each index, rightSum = total - leftSum - nums[i]. If leftSum equals rightSum, that index is the pivot."

---

## Key Insight

```text
Total Sum already contains everything.

Use it to derive missing information.
```

---

## Connection To Next Variation

LC1480:

```text
Build Prefix Sum
```

↓

LC303:

```text
Query Prefix Sum
```

↓

LC724:

```text
Compare Left and Right Regions
```

↓

Next:

```text
LC560 - Subarray Sum Equals K
```

This is where Prefix Sum becomes an interview-level pattern:

```text
Prefix Sum
+
HashMap
```

and unlocks dozens of Medium and Hard problems.

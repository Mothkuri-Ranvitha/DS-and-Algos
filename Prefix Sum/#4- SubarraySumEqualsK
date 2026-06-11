# Variation 4: Prefix Sum + HashMap

## LeetCode

**LC560 - Subarray Sum Equals K**

Difficulty: Medium

---

## Problem Statement

Given an integer array `nums` and an integer `k`, return the total number of continuous subarrays whose sum equals `k`.

Example:

```text
Input:

nums = [1,1,1]

k = 2

Output:

2
```

Explanation:

```text
[1,1]
[1,1]
```

Two valid subarrays.

---

## Why Does This Problem Exist?

LC1480 taught:

```text
Build Prefix Sum
```

LC303 taught:

```text
Range Sum Query
```

LC724 taught:

```text
Compare Regions
```

LC560 teaches:

```text
Count Subarrays Efficiently
```

This is the first true interview-level Prefix Sum problem.

---

## Brute Force Thinking

For every starting index:

Try every ending index.

Calculate subarray sum.

Example:

```text
[1,2,3]
```

Check:

```text
[1]

[1,2]

[1,2,3]

[2]

[2,3]

[3]
```

Time Complexity:

```text
O(N²)
```

Too slow.

---

## Core Observation

Suppose:

```text
Current Prefix Sum = 10

k = 3
```

Question:

```text
What previous prefix sum do I need?
```

Think:

```text
CurrentPrefix - PreviousPrefix

=

k
```

Substitute:

```text
10 - PreviousPrefix

=

3
```

Therefore:

```text
PreviousPrefix

=

7
```

Important discovery:

If a prefix sum of 7 existed earlier,

then the subarray between them has sum 3.

---

## The Golden Formula

```text
CurrentPrefix - PreviousPrefix = K
```

Rearranging:

```text
PreviousPrefix

=

CurrentPrefix - K
```

This is the entire problem.

Memorize the meaning.

Not the formula.

---

## Intuition

Imagine:

```text
Current Prefix = 15

Need Subarray Sum = 5
```

Ask:

```text
What old prefix should exist
so that removing it leaves 5?
```

Answer:

```text
15 - 5

=

10
```

If prefix 10 exists before,

we found a valid subarray.

---

## Visual Understanding

Array:

```text
[1] [2] [3]
```

Prefix:

```text
1

3

6
```

Need:

```text
k = 3
```

At:

```text
Prefix = 6
```

Need:

```text
6 - 3

=

3
```

Does Prefix 3 exist?

YES.

Therefore:

```text
Subarray Sum = 3
```

Found.

---

## Recognition Signals

Think:

```text
Prefix Sum + HashMap
```

when you see:

* Count Subarrays
* Sum Equals K
* Continuous Subarray
* Negative Numbers Exist
* Need Number of Ways

Keywords:

```text
count subarrays

sum equals k

continuous subarray

number of subarrays
```

---

## Why Sliding Window Fails?

Consider:

```text
[1,-1,2]
```

Negative numbers exist.

Window expansion/shrinking becomes unpredictable.

Sliding Window breaks.

Prefix Sum still works.

This is a huge interview clue.

---

## Mental Model

```text
Current Prefix Known

↓

Need Previous Prefix

↓

CurrentPrefix - K

↓

Check HashMap

↓

Count Answer
```

---

## Why HashMap?

Question:

```text
Have we seen

CurrentPrefix - K

before?
```

Need instant lookup.

HashMap provides:

```text
O(1)
```

search.

---

## How To Solve

### Step 1

Maintain:

```text
prefixSum
```

---

### Step 2

Store frequencies of prefix sums.

HashMap:

```text
Prefix Sum

↓

Count
```

---

### Step 3

For every element:

Update:

```text
prefixSum += nums[i]
```

---

### Step 4

Check:

```text
prefixSum - k
```

exists?

If yes:

Add frequency to answer.

---

### Step 5

Store current prefix sum.

Continue.

---

## Most Important Initialization

Before starting:

```text
map.put(0,1);
```

Why?

Suppose:

```text
PrefixSum = k
```

at current index.

Then:

```text
PrefixSum - k = 0
```

Need Prefix 0 available.

Without this line many test cases fail.

---

## Code

```java
class Solution {

    public int subarraySum(int[] nums, int k) {

        HashMap<Integer,Integer> map =
                new HashMap<>();

        map.put(0,1);

        int prefixSum = 0;
        int count = 0;

        for(int num : nums) {

            prefixSum += num;

            if(map.containsKey(prefixSum - k)) {
                count += map.get(prefixSum - k);
            }

            map.put(
                    prefixSum,
                    map.getOrDefault(prefixSum,0)+1
            );
        }

        return count;
    }
}
```

---

## Dry Run

Input:

```text
nums = [1,1,1]

k = 2
```

Initialize:

```text
map

{0:1}
```

---

Element:

```text
1
```

Prefix:

```text
1
```

Need:

```text
1-2

=

-1
```

Not found.

Store:

```text
{0:1,1:1}
```

---

Element:

```text
1
```

Prefix:

```text
2
```

Need:

```text
2-2

=

0
```

Found.

Frequency:

```text
1
```

Count:

```text
1
```

Store:

```text
{0:1,1:1,2:1}
```

---

Element:

```text
1
```

Prefix:

```text
3
```

Need:

```text
3-2

=

1
```

Found.

Frequency:

```text
1
```

Count:

```text
2
```

Answer:

```text
2
```

---

## Time Complexity

Single traversal:

```text
O(N)
```

HashMap operations:

```text
O(1)
```

Average.

Overall:

```text
O(N)
```

---

## Space Complexity

HashMap stores prefix sums.

```text
O(N)
```

---

## Common Mistakes

### Mistake 1

Forgetting:

```text
map.put(0,1)
```

Most common bug.

---

### Mistake 2

Using Sliding Window.

Fails with negative numbers.

---

### Mistake 3

Storing only existence.

Need frequency.

Because same prefix sum may appear multiple times.

---

### Mistake 4

Updating map before checking.

Always:

```text
Check Answer

↓

Store Prefix
```

---

## Interview Explanation

"I observed that if a subarray sum equals k, then CurrentPrefix - PreviousPrefix = k. Rearranging gives PreviousPrefix = CurrentPrefix - k. So for every prefix sum, I check whether CurrentPrefix - k has occurred before. A HashMap stores frequencies of previous prefix sums, allowing O(1) lookups and an overall O(N) solution."

---

## Key Insight

```text
CurrentPrefix - PreviousPrefix = K
```

Whenever you see:

```text
Count Subarrays

Sum = K
```

this formula should immediately come to mind.

---

## Connection To Next Variation

LC560 teaches:

```text
Prefix Sum
+
HashMap
```

Next:

```text
LC930 - Binary Subarrays With Sum
```

teaches a deeper idea:

```text
Prefix Frequency Counting
```

where the same prefix can contribute multiple answers.

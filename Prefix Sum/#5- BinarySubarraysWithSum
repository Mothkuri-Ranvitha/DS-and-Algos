# Variation 5: Prefix Frequency Counting

## LeetCode

**LC930 - Binary Subarrays With Sum**

Difficulty: Medium

---

## Problem Statement

Given a binary array `nums` and an integer `goal`, return the number of non-empty subarrays whose sum equals `goal`.

Example:

```text
Input:

nums = [1,0,1,0,1]

goal = 2

Output:

4
```

Valid subarrays:

```text
[1,0,1]

[1,0,1,0]

[0,1,0,1]

[1,0,1]
```

Answer:

```text
4
```

---

## Why Does This Problem Exist?

LC560 taught:

```text
Find subarrays with sum K
```

LC930 teaches:

```text
One prefix sum can generate
multiple answers.
```

This is a very important interview observation.

---

## First Thought

Looks exactly like:

```text
LC560
```

Because we need:

```text
Subarray Sum = Goal
```

Immediately think:

```text
CurrentPrefix - PreviousPrefix = Goal
```

---

## Core Observation

Suppose:

```text
Current Prefix = 5

Goal = 2
```

Need:

```text
Previous Prefix

=

5 - 2

=

3
```

Question:

How many times has Prefix 3 appeared?

Suppose:

```text
Prefix 3 appeared

3 times
```

Then:

```text
Current Prefix 5
```

creates:

```text
3 valid subarrays
```

at once.

This is the big idea.

---

## Intuition

In LC560 we asked:

```text
Does required prefix exist?
```

In LC930 we ask:

```text
How many times does it exist?
```

Because every occurrence creates a valid subarray.

---

## Visual Understanding

Array:

```text
[1,0,1,0,1]
```

Prefix:

```text
1

1

2

2

3
```

Notice:

```text
Prefix 1

appears twice
```

and

```text
Prefix 2

appears twice
```

Repeated prefix sums are useful.

Each occurrence represents a possible starting point.

---

## The Golden Formula

Same formula as LC560:

```text
CurrentPrefix - PreviousPrefix = Goal
```

Rearrange:

```text
PreviousPrefix

=

CurrentPrefix - Goal
```

Difference:

```text
Count frequency
instead of existence.
```

---

## Recognition Signals

Think:

```text
Prefix Sum + Frequency Map
```

when you see:

* Count Subarrays
* Number of Ways
* Binary Array
* Sum Equals Goal
* Total Count Required

Keywords:

```text
count

number of subarrays

goal

binary array

ways
```

---

## Mental Model

```text
Current Prefix Known

↓

Need CurrentPrefix - Goal

↓

How Many Times Seen?

↓

Add Frequency

↓

Store Current Prefix
```

---

## Why Frequency Matters

Suppose:

```text
Map

{3 : 4}
```

Meaning:

```text
Prefix Sum 3

appeared 4 times
```

Current:

```text
Prefix = 5

Goal = 2
```

Need:

```text
5 - 2 = 3
```

Found.

Frequency:

```text
4
```

Immediately:

```text
count += 4
```

because all 4 previous positions create valid subarrays.

---

## How To Solve

### Step 1

Store prefix frequencies.

```text
PrefixSum

↓

Frequency
```

---

### Step 2

Initialize:

```text
map.put(0,1)
```

---

### Step 3

Build running prefix.

```text
prefix += num
```

---

### Step 4

Find:

```text
prefix - goal
```

---

### Step 5

Add its frequency.

---

### Step 6

Store current prefix.

Continue.

---

## Code

```java
class Solution {

    public int numSubarraysWithSum(
            int[] nums,
            int goal) {

        HashMap<Integer,Integer> map =
                new HashMap<>();

        map.put(0,1);

        int prefix = 0;
        int count = 0;

        for(int num : nums) {

            prefix += num;

            count +=
                    map.getOrDefault(
                            prefix - goal,
                            0
                    );

            map.put(
                    prefix,
                    map.getOrDefault(prefix,0)+1
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
nums

[1,0,1,0,1]

goal = 2
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
0
```

Prefix:

```text
1
```

Need:

```text
-1
```

Not found.

Store:

```text
{0:1,1:2}
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
0
```

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
{0:1,1:2,2:1}
```

---

Element:

```text
0
```

Prefix:

```text
2
```

Need:

```text
0
```

Frequency:

```text
1
```

Count:

```text
2
```

Store:

```text
{0:1,1:2,2:2}
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
1
```

Frequency:

```text
2
```

Count:

```text
4
```

Final Answer:

```text
4
```

---

## Time Complexity

Single traversal:

```text
O(N)
```

HashMap lookup:

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

Using:

```text
containsKey()
```

instead of frequency.

Need:

```text
getOrDefault()
```

because multiple occurrences matter.

---

### Mistake 2

Forgetting:

```text
map.put(0,1)
```

Important initialization.

---

### Mistake 3

Not understanding why frequency adds multiple answers.

Every occurrence of a valid prefix creates another valid subarray.

---

### Mistake 4

Thinking this is different from LC560.

Actually:

```text
LC930

=

LC560
+
Frequency Thinking
```

---

## Interview Explanation

"I use Prefix Sum with a HashMap storing frequencies of previous prefix sums. For every current prefix, I need a previous prefix equal to CurrentPrefix - Goal. The frequency of that prefix tells me how many valid subarrays end at the current position. This gives an O(N) solution."

---

## Key Insight

```text
One prefix sum can create
multiple answers.
```

Frequency matters.

Not just existence.

---


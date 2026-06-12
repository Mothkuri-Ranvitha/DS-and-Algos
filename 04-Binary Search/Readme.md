# Binary Search

> Eliminate half of the search space at every step.

---

# Why Does This Pattern Exist?

Suppose you need to find a number in a sorted array.

Brute Force:

```text
1 3 5 7 9 11 13

Search 11

Check:
1 → 3 → 5 → 7 → 9 → 11
```

Time:

```text
O(N)
```

Can we do better?

Since the array is sorted:

```text
1 3 5 7 9 11 13
      ↑
    Middle
```

If target > middle:

```text
Discard Left Half
```

If target < middle:

```text
Discard Right Half
```

Every step removes half the search space.

Time becomes:

```text
O(log N)
```

---

# Core Intuition

Think:

```text
Sorted Data
      ↓
Can I eliminate half?
```

Binary Search is not about finding a number.

Binary Search is about:

```text
Reducing Search Space
```

---

# Real Life Analogy

Finding a word in a dictionary.

You don't start from page 1.

You open near the middle.

```text
Target after middle?

Go Right

Target before middle?

Go Left
```

Repeat.

---

# Recognition Signals

Think Binary Search when you see:

### Direct Signals

* Sorted Array
* Sorted List
* Sorted Matrix
* Search Element

---

### Hidden Signals

* Minimum Possible
* Maximum Possible
* Smallest Valid Answer
* Largest Valid Answer
* Capacity
* Speed
* Threshold

These usually indicate:

```text
Binary Search On Answer
```

---

# Mental Model

Whenever you see a problem:

### Question 1

```text
Is data sorted?
```

If YES:

```text
Think Binary Search
```

---

### Question 2

```text
Can I eliminate half?
```

If YES:

```text
Think Binary Search
```

---

### Question 3

```text
Am I searching for an answer value?
```

Example:

```text
Minimum Speed

Minimum Capacity

Maximum Distance
```

If YES:

```text
Binary Search On Answer
```

---

# Generic Template

```java
int low = 0;
int high = n - 1;

while(low <= high){

    int mid =
        low + (high - low)/2;

    if(nums[mid] == target)
        return mid;

    else if(nums[mid] < target)
        low = mid + 1;

    else
        high = mid - 1;
}
```

---

# Major Variations

## 1. Classic Binary Search

Goal:

```text
Find target in sorted array.
```

Examples:

```text
LC704 Binary Search
LC35 Search Insert Position
```

---

## 2. Lower Bound

Goal:

```text
Find first valid position.
```

Examples:

```text
LC35 Search Insert Position
LC34 First and Last Position
```

Visual:

```text
1 2 2 2 3

First 2
     ↑
```

---

## 3. Upper Bound

Goal:

```text
Find last valid position.
```

Examples:

```text
LC34 First and Last Position
```

Visual:

```text
1 2 2 2 3

      ↑
   Last 2
```

---

## 4. Rotated Sorted Array

Array remains sorted but rotated.

Example:

```text
4 5 6 7 0 1 2
```

Observation:

```text
One half is always sorted.
```

Examples:

```text
LC33 Search in Rotated Sorted Array
LC153 Find Minimum in Rotated Array
```

---

## 5. Binary Search On Answer

Most important variation.

We are NOT searching array.

We are searching answer space.

Example:

```text
Minimum Speed

Maximum Distance

Minimum Capacity
```

Examples:

```text
LC875 Koko Eating Bananas

LC1011 Capacity To Ship Packages

LC410 Split Array Largest Sum
```

Mental Model:

```text
Answer Possible?

YES
↓
Try Smaller

NO
↓
Try Bigger
```

---

## 6. Peak / Mountain Problems

Observation:

```text
Array increases

Then decreases
```

Example:

```text
1 3 5 8 7 4 2
      ↑
     Peak
```

Examples:

```text
LC162 Find Peak Element

LC852 Peak Index in Mountain Array
```

---

# Problem Roadmap

## Foundation

```text
LC704 Binary Search

LC35 Search Insert Position
```

---

## Intermediate

```text
LC34 First and Last Position

LC33 Search in Rotated Array

LC153 Find Minimum in Rotated Array
```

---

## Advanced

```text
LC875 Koko Eating Bananas

LC1011 Capacity To Ship Packages

LC410 Split Array Largest Sum
```

---

# Complexity

For most Binary Search problems:

```text
Time  : O(log N)

Space : O(1)
```

---

# Common Mistakes

### Mistake 1

Wrong Mid Calculation

Bad:

```java
int mid = (low + high)/2;
```

Better:

```java
int mid =
    low + (high-low)/2;
```

---

### Mistake 2

Infinite Loop

Wrong boundary updates.

Always verify:

```text
low = mid + 1

high = mid - 1
```

---

### Mistake 3

Not Identifying Search Space

Many interview problems do NOT mention:

```text
Binary Search
```

You must recognize:

```text
Minimum Possible

Maximum Possible

Smallest Valid
```

These are strong hints.

---

# Interview Explanation

"Since the search space is sorted (or monotonic), we can eliminate half of the possibilities after every comparison. Therefore Binary Search reduces the complexity from O(N) to O(log N)."

---

# Pattern Tracker

```text
Pattern:
Binary Search

Core Idea:
Eliminate Half

Recognition:
Sorted Data
Monotonic Condition
Minimum/Maximum Answer

Goal:
Reduce Search Space

Complexity:
O(log N)
```

---

# One-Line Revision

```text
Binary Search =
Can I throw away half the possibilities?
```

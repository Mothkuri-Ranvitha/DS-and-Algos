# Sliding Window

> Don't rebuild subarrays. Slide the window.

---

## Why Does This Pattern Exist?

Many problems ask:

* Subarrays
* Substrings
* Longest
* Shortest
* Maximum
* Minimum

Brute force checks every possible window.

```text
O(N²)
```

Sliding Window reuses previous work and processes elements only once.

---

## Core Intuition

Maintain a window:

```text
[L ...... R]
```

Instead of creating new subarrays repeatedly, move the boundaries.

---

## Recognition Signals

Think Sliding Window when you see:

* Subarray
* Substring
* Consecutive elements
* Longest
* Shortest
* Maximum
* Minimum
* At Most K
* At Least K
* Exactly K

---

## Types of Sliding Window

### 1. Fixed Window

Window size never changes.

Example:

```text
Size = K
```

Visual:

```text
[1 2 3] 4 5

1 [2 3 4] 5

1 2 [3 4 5]
```

Problems:

* LC643 Maximum Average Subarray I
* LC1456 Maximum Number of Vowels in a Substring of Given Length
* LC1343 Number of Sub-arrays of Size K

---

### 2. Variable Window

Window expands and shrinks.

Visual:

```text
Expand →

[L ...... R]

Condition Breaks

Shrink ←
```

Problems:

* LC209 Minimum Size Subarray Sum
* LC3 Longest Substring Without Repeating Characters
* LC424 Longest Repeating Character Replacement
* LC1004 Max Consecutive Ones III
* LC76 Minimum Window Substring

---

## Generic Template

### Fixed Window

```java
for(int right = k; right < n; right++) {

    window += nums[right];
    window -= nums[right - k];
}
```

---

### Variable Window

```java
for(int right = 0; right < n; right++) {

    // expand

    while(conditionBroken) {

        // shrink
        left++;
    }
}
```

---

## Learning Order

### Fixed Window

1. LC643 Maximum Average Subarray I
2. LC1456 Maximum Number of Vowels
3. LC1343 Number of Subarrays of Size K

### Variable Window

1. LC209 Minimum Size Subarray Sum
2. LC3 Longest Substring Without Repeating Characters
3. LC424 Longest Repeating Character Replacement
4. LC1004 Max Consecutive Ones III
5. LC76 Minimum Window Substring

---

## Complexity

```text
Time  : O(N)

Space : O(1) to O(K)
```

---

## Pattern Tracker

```text
Pattern:
Sliding Window

Core Idea:
Maintain a window instead of rebuilding it.

Recognition:
Subarray
Substring
Longest
Shortest
At Most K
At Least K

Goal:
Reduce O(N²) to O(N)
```

---

## One-Line Revision

```text
Sliding Window =
Expand, Shrink, Maintain.
```

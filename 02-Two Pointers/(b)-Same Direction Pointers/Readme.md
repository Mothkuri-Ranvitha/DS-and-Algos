# Same Direction Pointers

> One pointer explores. One pointer maintains.

---

## Why Does This Pattern Exist?

Many interview problems ask:

* Remove duplicates
* Move zeroes
* Remove elements
* Modify array in-place

Instead of creating a new array, we use two pointers moving in the same direction to rebuild the array efficiently.

---

## Core Intuition

Think:

```text
Fast Pointer → Reads

Slow Pointer → Writes
```

Visual:

```text
[1,1,2,2,3]

 S
 F
```

Fast scans the array.

*Slow maintains the valid portion.*

Result:

```text
[1,2,3,_,_]
```

---

## Recognition Signals

Use Same Direction Pointers when you see:

* In-place modification
* Remove duplicates
* Remove element
* Move zeroes
* Compact array
* Return new length
* O(1) extra space

---

## Generic Template

```java
int slow = 0;

for(int fast = 0; fast < nums.length; fast++) {

    if(valid(nums[fast])) {

        nums[slow] = nums[fast];
        slow++;
    }
}
```

### Mental Model

```text
Fast Reads
      ↓
Useful?
      ↓
Slow Writes
```

---

## Major Variations

### 1. Fast-Slow Compression

Keep useful values.

Examples:

* LC26 Remove Duplicates from Sorted Array
* LC27 Remove Element

Example:

```text
[1,1,2,2,3]

↓

[1,2,3]
```

---

### 2. Move Elements

Move special values to one side.

Examples:

* LC283 Move Zeroes
* LC905 Sort Array By Parity

Example:

```text
[0,1,0,3,12]

↓

[1,3,12,0,0]
```

---

### 3. Partitioning

Maintain multiple regions.

Examples:

* LC75 Sort Colors

Example:

```text
[2,0,2,1,1,0]

↓

[0,0,1,1,2,2]
```

---

## Problem Roadmap

### Foundation

* LC26 Remove Duplicates
* LC27 Remove Element

### Intermediate

* LC283 Move Zeroes
* LC905 Sort Array By Parity

### Advanced

* LC75 Sort Colors

---

## Complexity

```text
Time  : O(N)

Space : O(1)
```

---

## Pattern Tracker

```text
Pattern:
Same Direction Pointers

Core Idea:
Fast Reads
Slow Writes

Recognition:
In-place modification

Goal:
Rebuild array without extra space
```

---

## One-Line Revision

```text
Same Direction Pointers =
One pointer discovers,
the other pointer maintains.
```


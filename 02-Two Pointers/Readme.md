# Pattern #2: Two Pointers

> "Don't search everywhere. Eliminate impossible answers."

---

# Why Does This Pattern Exist?

The brute force solution for many array and string problems is:

```text
Try every possibility.
```

Example:

```text
Find a pair with target sum.
```

Brute Force:

```text
Check every pair.
```

```text
O(N²)
```

Most interview problems are designed so that:

```text
Many possibilities can be eliminated
without checking them.
```

Two Pointers helps us do exactly that.

Instead of exploring everything:

```text
Move pointers intelligently.
```

and reduce:

```text
O(N²)

↓

O(N)
```

---

# Core Intuition

Think of two pointers as:

```text
Two detectives searching from
different directions.
```

Example:

```text
[1,2,3,4,5,6,7,8]
```

Target:

```text
9
```

Start:

```text
L=1

R=8
```

Sum:

```text
1+8=9
```

Found.

No need to check:

```text
1+2
1+3
1+4
1+5
...
```

We eliminate huge parts of the search space.

---

# The Golden Question

Whenever you see a problem ask:

```text
Can I move pointers
instead of checking everything?
```

If yes:

```text
Think Two Pointers.
```

---

# Recognition Signals

Think Two Pointers when you see:

### Arrays

```text
Sorted Array

Pair Sum

Triplets

In-place Modification

Remove Duplicates

Move Elements
```

### Strings

```text
Palindrome

Reverse String

Substring Problems
```

### Linked Lists

```text
Cycle Detection

Middle Node

Fast-Slow Movement
```

---

# The Two Pointers Family

Many people think Two Pointers is one pattern.

Wrong.

It contains four major patterns.

```text
Two Pointers
│
├── Opposite Direction
│
├── Same Direction
│
├── Sliding Window
│
└── Floyd Cycle Detection
```

---

# 1. Opposite Direction Pointers

Pointers start from opposite ends.

Visual:

```text
L           R

[1 2 3 4 5 6 7]
 ↑           ↑
```

Move inward.

---

## Mental Model

```text
Search Space Elimination
```

Example:

```text
Target Sum

Palindrome

Reverse Array
```

---

## Recognition Signals

```text
Sorted Array

Pair Problems

Palindrome

Reverse String
```

---

## Problems

### Foundation

```text
LC125 Valid Palindrome

LC344 Reverse String
```

---

### Intermediate

```text
LC167 Two Sum II

LC977 Squares of Sorted Array
```

---

### Advanced

```text
LC11 Container With Most Water

LC15 3Sum

LC18 4Sum

LC42 Trapping Rain Water
```

---

# 2. Same Direction Pointers

Both pointers move left → right.

Visual:

```text
S
F

0 1 2 3 4 5 6
```

Later:

```text
    S

          F
```

---

## Mental Model

```text
One Pointer Reads

One Pointer Maintains
```

---

## Recognition Signals

```text
Remove Duplicates

Move Zeroes

Remove Elements

Compaction Problems

In-place Array Modification
```

---

## Problems

```text
LC26 Remove Duplicates

LC27 Remove Element

LC283 Move Zeroes

LC905 Sort Array By Parity
```

---

# 3. Sliding Window

Sliding Window evolved from Two Pointers.

Treat it as a separate sub-pattern.

---

## Core Idea

Maintain a window:

```text
[L........R]
```

instead of rebuilding subarrays repeatedly.

---

## Two Types

### Fixed Window

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

---

Recognition:

```text
Exactly K

Length K

Size K
```

---

Problems:

```text
LC643 Maximum Average Subarray I

LC1456 Maximum Number of Vowels

LC1343 Number of Subarrays of Size K
```

---

### Variable Window

Window expands and shrinks.

Visual:

```text
Expand →

[L.......R]

Condition Breaks

Shrink ←
```

---

Recognition:

```text
Longest

Shortest

At Most K

At Least K

Distinct Characters
```

---

Problems:

```text
LC209 Minimum Size Subarray Sum

LC3 Longest Substring Without Repeating Characters

LC424 Longest Repeating Character Replacement

LC1004 Max Consecutive Ones III

LC76 Minimum Window Substring
```

---

# 4. Floyd Cycle Detection

Special Fast-Slow Pointer pattern.

---

## Mental Model

Slow moves:

```text
1 step
```

Fast moves:

```text
2 steps
```

If a cycle exists:

```text
Fast eventually catches Slow.
```

---

## Recognition Signals

```text
Cycle

Loop

Duplicate Number

Linked List Cycle
```

---

## Problems

```text
LC141 Linked List Cycle

LC142 Linked List Cycle II

LC287 Find Duplicate Number

LC202 Happy Number
```

---

# Learning Order

Follow this exact order.

```text
1. Opposite Direction

↓

2. Same Direction

↓

3. Fixed Sliding Window

↓

4. Variable Sliding Window

↓

5. Floyd Cycle Detection
```

Do NOT jump to Sliding Window first.

The intuition comes from understanding pointer movement.

---

# Repository Structure

```text
02-Two-Pointers/

README.md

├── 01-Opposite-Direction/
│
├── 02-Same-Direction/
│
├── 03-Sliding-Window/
│   │
│   ├── Fixed-Window/
│   │
│   └── Variable-Window/
│
└── 04-Floyd-Cycle-Detection/
```

---

# Pattern Tracker

```text
Pattern:
Two Pointers

Core Idea:
Move pointers intelligently
instead of checking everything.

Goal:
Reduce O(N²) to O(N)

Recognition Signals:

✓ Sorted Array

✓ Pair Sum

✓ Palindrome

✓ Reverse String

✓ Remove Duplicates

✓ In-place Modification

✓ Window Problems

✓ Cycle Detection

Mental Model:

Brute Force

↓

Too Many Possibilities

↓

Eliminate Search Space

↓

Move Pointers

↓

Find Answer
```

---

# One-Line Revision

```text
Two Pointers is the art of
eliminating impossible answers
without checking them.
```

---

# Challenge Goal

After completing this pattern, you should be able to instantly recognize:

```text
Opposite Direction

Same Direction

Fixed Window

Variable Window

Floyd Cycle Detection
```

within 30 seconds of reading an interview problem.

That is the real objective of this pattern.

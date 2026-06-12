# Hashing

> Remember information to avoid repeated work.

---

## What is Hashing?

Hashing is a technique used to store and retrieve information in near O(1) time.

Instead of repeatedly searching through data:

```text
Search Again
Search Again
Search Again
```

we store useful information once and access it instantly.

This allows many O(N²) solutions to become O(N).

---

## Why Does This Pattern Exist?

Consider this problem:

```text
Find whether an array contains duplicates.
```

Without hashing:

```text
Compare every element
with every other element.

Time: O(N²)
```

With hashing:

```text
Store seen values.

If value already exists,
duplicate found.
```

Time becomes:

```text
O(N)
```

Hashing is essentially:

```text
Memory
   ↓
for
Speed
```

---

## Core Intuition

Think of HashMap and HashSet as memory.

Instead of asking:

```text
Have I seen this before?
```

and searching again,

we simply remember it.

```text
Store Once
      ↓
Retrieve Instantly
```

---

## Recognition Signals

Think Hashing when you see:

* Duplicates
* Frequency Count
* Pair Finding
* Fast Lookup
* Grouping
* Mapping
* Unique Elements
* O(1) Search Needed
* Count Occurrences
* Previous Occurrence Matters

---

## Interview Mental Model

When reading a problem ask:

### Question 1

```text
Do I need to remember
something seen earlier?
```

If YES:

```text
HashSet
or
HashMap
```

---

### Question 2

```text
Am I counting frequencies?
```

If YES:

```text
HashMap<Character, Integer>

HashMap<Integer, Integer>
```

---

### Question 3

```text
Do I need fast lookup?
```

If YES:

```text
HashSet
HashMap
```

---

### Question 4

```text
Do I need to group
similar items together?
```

If YES:

```text
HashMap<Key, List>
```

---

## Major Variations

### 1. Frequency Counting

Count occurrences of elements.

Common Questions:

```text
How many times?
Most frequent?
Same frequency?
```

Examples:

```text
LC242 Valid Anagram
LC169 Majority Element
LC1207 Unique Number of Occurrences
```

---

### 2. Lookup Problems

Store previous values and retrieve instantly.

Common Questions:

```text
Have I seen this before?
Can I find a complement?
```

Examples:

```text
LC1 Two Sum
LC219 Contains Duplicate II
```

---

### 3. Duplicates & Uniqueness

Detect repeated or unique elements.

Common Questions:

```text
Duplicate exists?
Unique count?
Longest unique sequence?
```

Examples:

```text
LC217 Contains Duplicate
LC128 Longest Consecutive Sequence
```

---

### 4. Grouping & Mapping

Group related elements together.

Common Questions:

```text
Belong to same group?
Same pattern?
Same signature?
```

Examples:

```text
LC49 Group Anagrams
LC205 Isomorphic Strings
```

---

### 5. HashMap + Prefix Sum

Store previous prefix sums.

This is one of the most important Amazon patterns.

Common Questions:

```text
Subarray Sum
Count Subarrays
Equal Zeros and Ones
```

Examples:

```text
LC560 Subarray Sum Equals K
LC525 Contiguous Array
LC930 Binary Subarrays With Sum
```

---

### 6. HashMap + Sliding Window

Store frequencies inside a moving window.

Common Questions:

```text
Longest Substring
Minimum Window
Character Frequency
```

Examples:

```text
LC3 Longest Substring Without Repeating Characters
LC424 Character Replacement
LC76 Minimum Window Substring
```

---

## HashSet vs HashMap

### HashSet

Use when only existence matters.

Example:

```text
Seen before?
Duplicate exists?
```

```java
HashSet<Integer> set = new HashSet<>();
```

---

### HashMap

Use when additional information is needed.

Example:

```text
Frequency
Index
Count
Mapping
```

```java
HashMap<Integer, Integer> map = new HashMap<>();
```

---

## Complexity

Average Case:

```text
Insert  : O(1)

Search  : O(1)

Delete  : O(1)
```

Space:

```text
O(N)
```

---

## Problem Roadmap

### Foundation

```text
LC217 Contains Duplicate
LC242 Valid Anagram
LC1 Two Sum
```

---

### Intermediate

```text
LC49 Group Anagrams
LC128 Longest Consecutive Sequence
```

---

### Advanced

```text
LC560 Subarray Sum Equals K
LC525 Contiguous Array
LC3 Longest Substring Without Repeating Characters
```

---

## Pattern Tracker

```text
Pattern:
Hashing

Core Idea:
Remember information
to avoid repeated work

Recognition Signals:
Duplicates
Frequency
Lookup
Grouping
Mapping

Primary Tools:
HashSet
HashMap

Goal:
Reduce O(N²)
to O(N)
```

---

## One-Line Revision

```text
Hashing =
Store information once,
retrieve it instantly.
```

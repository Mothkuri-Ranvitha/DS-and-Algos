# Prefix Sum

> "Pay once. Use many times."

---

# Why Does This Pattern Exist?

Imagine an array:

```text
[2, 3, 1, 5, 4]
```

Suppose someone asks:

```text
Sum from index 1 to 3?
```

We calculate:

```text
3 + 1 + 5 = 9
```

Easy.

But what if there are 10,000 such queries?

```text
Sum(1,3)
Sum(0,4)
Sum(2,4)
Sum(1,2)
...
```

We keep repeating the same additions.

Prefix Sum exists to eliminate repeated calculations.

Instead of recomputing sums again and again, we precompute cumulative information once and reuse it.

---

# Core Intuition

Store answers to future questions before they are asked.

Normal Approach:

```text
Question
↓
Calculate
↓
Answer
```

Prefix Sum Approach:

```text
Precompute
↓
Store
↓
Instant Answer
```

Think of it as:

```text
Pay once.
Use many times.
```

---

# Real Life Analogy

Suppose you save money every day.

```text
Day1 = 100
Day2 = 50
Day3 = 200
Day4 = 150
```

Instead of remembering daily amounts:

```text
Day1 = 100
Day2 = 150
Day3 = 350
Day4 = 500
```

Now you can instantly find how much money was earned between two days.

That cumulative total is exactly what Prefix Sum stores.

---

# Visual Understanding

Array:

```text
Index

0   1   2   3   4

[2] [3] [1] [5] [4]
```

Build Prefix:

```text
Prefix[0] = 2

Prefix[1] = 2+3 = 5

Prefix[2] = 2+3+1 = 6

Prefix[3] = 2+3+1+5 = 11

Prefix[4] = 2+3+1+5+4 = 15
```

Result:

```text
Array

[2] [3] [1] [5] [4]

Prefix

[2] [5] [6] [11] [15]
```

Meaning:

```text
Prefix[i]
=
Sum of everything from index 0 to i
```

---

# The Magic Formula

Need sum from index L to R?

```text
Range Sum

=
Prefix[R] - Prefix[L-1]
```

Example:

```text
Array

[2] [3] [1] [5] [4]

Need sum(1,3)

3 + 1 + 5
```

Using Prefix:

```text
Prefix[3] = 11

Prefix[0] = 2

11 - 2 = 9
```

Answer found instantly.

---

# Recognition Signals

When you see these clues, think Prefix Sum.

✅ Range Sum Queries

```text
Find sum from L to R
```

---

✅ Running Total

```text
Cumulative score
Cumulative rainfall
Cumulative sales
```

---

✅ Multiple Queries

```text
Many range queries on same array
```

---

✅ Continuous Subarray

```text
Subarray Sum
Subarray Count
```

---

✅ Need O(1) Query Answer

Repeated calculations are expensive.

---

# Pattern Boundaries

Use Prefix Sum When:

✅ Range calculations

✅ Subarray problems

✅ Repeated sum queries

✅ Cumulative information is useful

---

Do NOT Use Prefix Sum When:

❌ Searching elements

Use:

```text
Binary Search
HashMap
```

---

❌ Frequent updates in array

Use:

```text
Fenwick Tree
Segment Tree
```

---

# Mental Model

Whenever you see a problem:

```text
Problem
↓
Repeated Calculation?
↓
Can I store previous work?
↓
YES
↓
Prefix Sum
```

---

# Pattern Evolution

Prefix Sum appears in multiple forms.

```text
Running Sum
        ↓
Range Query
        ↓
Left vs Right Comparison
        ↓
Prefix + HashMap
        ↓
Subarray Counting
        ↓
2D Prefix Sum
```

Do not memorize problems.

Understand the evolution.

---

# Common Variations

## Variation 1: Running Sum

Goal:

```text
Build cumulative values.
```

Example:

```text
LC1480 Running Sum
```

---

## Variation 2: Range Sum Query

Goal:

```text
Answer sum(L,R) quickly.
```

Example:

```text
LC303 Range Sum Query
```

---

## Variation 3: Left Sum vs Right Sum

Goal:

```text
Compare two sides efficiently.
```

Example:

```text
LC724 Pivot Index
```

---

## Variation 4: Prefix + HashMap

Goal:

```text
Find subarray sum = K
```

Observation:

```text
CurrentPrefix - PreviousPrefix = K
```

Example:

```text
LC560 Subarray Sum Equals K
```

---

## Variation 5: Prefix Frequency Counting

Goal:

```text
Count valid subarrays.
```

Example:

```text
LC930 Binary Subarrays With Sum
```

---

## Variation 6: 2D Prefix Sum

Goal:

```text
Range sum in matrix.
```

Used in:

```text
Matrix query problems
```

---

# Common Mistakes

### Mistake 1

Off-by-one errors.

Always verify:

```text
Prefix[R] - Prefix[L-1]
```

---

### Mistake 2

Forgetting Prefix[0].

Many HashMap solutions fail because:

```text
Prefix Sum 0
```

was not stored initially.

---

### Mistake 3

Using Sliding Window when negatives exist.

Sliding Window often fails with negative numbers.

Prefix Sum usually handles them.

---

# Interview Explanation

"Prefix Sum is a preprocessing technique used to avoid repeated calculations. Instead of computing range sums repeatedly, we store cumulative sums. This allows us to answer range queries in O(1). The same idea extends to subarray problems, counting problems, and matrix range queries."

---

# Problem Roadmap

## Level 1 — Foundation

LC1480 Running Sum

Teaches:
Building Prefix Arrays

---

## Level 2 — Range Query

LC303 Range Sum Query

Teaches:
Prefix[R] - Prefix[L-1]

---

## Level 3 — Comparison

LC724 Pivot Index

Teaches:
Left Sum vs Right Sum

---

## Level 4 — Prefix + HashMap

LC560 Subarray Sum Equals K

Teaches:
CurrentPrefix - PreviousPrefix

---

## Level 5 — Advanced Counting

LC930 Binary Subarrays With Sum

Teaches:
Frequency of Prefix Sums

---

# Revision Sheet

Recognition Signals:

* Range Sum
* Running Total
* Multiple Queries
* Continuous Subarray
* Subarray Sum

Core Formula:

```text
Prefix[R] - Prefix[L-1]
```

Advanced Formula:

```text
CurrentPrefix - PreviousPrefix = K
```

Key Insight:

```text
Store previous work.
Reuse it later.
```

Pattern Evolution:

```text
Running Sum
↓
Range Query
↓
Comparison
↓
HashMap
↓
Counting
↓
2D Prefix
```

One-Line Revision:

```text
Pay once. Use many times.
```





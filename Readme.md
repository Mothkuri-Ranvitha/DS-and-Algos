# Monotonic Stack

## What is a Monotonic Stack?

A Monotonic Stack is a special type of stack that always maintains its elements in a specific order while processing an array.

There are two types:

### 1. Monotonically Increasing Stack

Elements remain in increasing order.

```text
Bottom → Top

1 2 4 7
```

Used for:

* Next Smaller Element
* Previous Smaller Element
* Histogram Problems

---

### 2. Monotonically Decreasing Stack

Elements remain in decreasing order.

```text
Bottom → Top

9 7 5 2
```

Used for:

* Next Greater Element
* Previous Greater Element
* Daily Temperatures
* Stock Span

---

# Why Do We Need Monotonic Stack?

Many problems ask:

* Find nearest greater element
* Find nearest smaller element
* Find first greater element on the right
* Find first smaller element on the left
* Find boundary of expansion
* Find rectangle area
* Find distance to next greater element

A brute force solution usually requires:

```java
for(int i=0;i<n;i++)
    for(int j=i+1;j<n;j++)
```

Time Complexity:

```text
O(N²)
```

Monotonic Stack reduces this to:

```text
O(N)
```

because every element is pushed and popped at most once.

---

# Core Intuition

Consider:

```text
[2,1,3]
```

When processing:

```text
3
```

Can:

```text
1
```

ever become useful again?

No.

Why?

Because:

```text
3 is greater than 1
3 is closer to future elements
```

So 1 becomes useless.

We remove it.

This is the entire idea behind Monotonic Stack.

---

# Golden Rule

Whenever a new element arrives:

```text
Remove all useless elements
from the stack.
```

Then push the current element.

---

# How To Identify Monotonic Stack Problems

Look for keywords like:

```text
Next Greater

Next Smaller

Previous Greater

Previous Smaller

Nearest Greater

Nearest Smaller

Warmer Temperature

Stock Span

Histogram

Rectangle Area

Trapping Rain Water
```

If you see these phrases, think:

```text
MONOTONIC STACK
```

---

# How To Approach Any Monotonic Stack Problem

## Step 1

Identify what is required.

```text
Greater?
Smaller?
```

---

## Step 2

Identify direction.

```text
Next
→ Right Side

Previous
→ Left Side
```

---

## Step 3

Choose stack type.

| Requirement      | Stack Type |
| ---------------- | ---------- |
| Next Greater     | Decreasing |
| Previous Greater | Decreasing |
| Next Smaller     | Increasing |
| Previous Smaller | Increasing |

---

## Step 4

Maintain the stack.

For every element:

1. Remove useless elements.
2. Stack top becomes answer candidate.
3. Push current element.

---

# Monotonic Stack Variations

## Variation 1 — Nearest Greater / Smaller Elements

Find:

* Next Greater Element
* Next Smaller Element
* Previous Greater Element
* Previous Smaller Element

Core Idea:

```text
Find nearest valid candidate.
```

Problems:

* LC496 Next Greater Element I
* GFG Next Greater Element
* Previous Smaller Element

---

## Variation 2 — Circular Array Problems

Array behaves like a circle.

Example:

```text
[1,2,1]
```

For the last element, searching continues from the beginning.

Problems:

* LC503 Next Greater Element II

Technique:

```text
Traverse array twice.
```

---

## Variation 3 — Distance Based Problems

Need distance instead of value.

Example:

```text
How many positions away is
the next greater element?
```

Problems:

* LC739 Daily Temperatures

Technique:

```text
Store indices instead of values.
```

---

## Variation 4 — Span Problems

Need count of consecutive elements satisfying a condition.

Problems:

* LC901 Online Stock Span

Question:

```text
How many previous elements
can be included?
```

---

## Variation 5 — Boundary Problems

Need expansion limits for every element.

Questions:

```text
How far can this element
expand left and right?
```

Problems:

* LC84 Largest Rectangle in Histogram

Technique:

```text
Previous Smaller
+
Next Smaller
```

---

## Variation 6 — Rectangle Problems

Extension of boundary problems.

Problems:

* LC85 Maximal Rectangle

Technique:

```text
Convert matrix into histogram.
```

Apply:

```text
Largest Rectangle Histogram
```

repeatedly.

---

## Variation 7 — Water Trapping Problems

Need left boundary and right boundary.

Problems:

* LC42 Trapping Rain Water

Idea:

```text
Current bar becomes
right wall.

Stack provides
left wall.
```

Calculate trapped water.

---

## Variation 8 — Greedy + Monotonic Stack

Need lexicographically smallest result.

Problems:

* LC402 Remove K Digits
* LC316 Remove Duplicate Letters
* LC1081 Smallest Subsequence

Idea:

```text
If current element is better,

remove previous larger
elements.
```

---

# Learning Order

## Foundation

1. Next Greater Element
2. Next Smaller Element
3. Previous Greater Element
4. Previous Smaller Element

---

## Intermediate

1. LC496 Next Greater Element I
2. LC503 Next Greater Element II
3. LC739 Daily Temperatures
4. LC901 Online Stock Span

---

## Advanced

1. LC84 Largest Rectangle in Histogram
2. LC42 Trapping Rain Water
3. LC85 Maximal Rectangle
4. LC402 Remove K Digits

---

# Important Notes

### Every element is pushed once.

### Every element is popped once.

Therefore:

```text
Time Complexity = O(N)
```

for most monotonic stack problems.

---

# Pattern Summary

```text
Nearest Greater/Smaller
            ↓
      Monotonic Stack

Distance To Greater
            ↓
      Monotonic Stack

Stock Span
            ↓
      Monotonic Stack

Histogram Area
            ↓
      Monotonic Stack

Water Trapping
            ↓
      Monotonic Stack

Remove K Digits
            ↓
Monotonic Stack + Greedy
```

---

# One-Line Revision

Monotonic Stack = Maintain only useful candidates in sorted order so nearest greater/smaller queries can be answered in O(N).

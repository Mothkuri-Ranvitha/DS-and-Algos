# Binary Search Pattern

## Pattern Definition

Binary Search is an algorithm used to efficiently search within a sorted search space.

Instead of checking every possibility, Binary Search repeatedly eliminates half of the search space.

This reduces complexity from:

```text
O(N)
```

to:

```text
O(log N)
```

---

# Core Intuition

Suppose:

```text
[1,3,5,7,9,11,13]
```

Target:

```text
9
```

Instead of checking:

```text
1 → 3 → 5 → 7 → 9
```

check the middle:

```text
7
```

If:

```text
target > 7
```

discard the left half.

Search only:

```text
[9,11,13]
```

Every step removes half of the remaining search space.

---

# When Can Binary Search Be Used?

Most beginners think Binary Search only works on:

```text
Sorted Arrays
```

But interviews use Binary Search on:

```text
Sorted Arrays

Sorted Matrices

Rotated Arrays

Answer Space

Monotonic Functions

Partitions
```

The real requirement is:

```text
Search Space must be Monotonic
```

---

# Recognition Signals

Think Binary Search when you see:

* Sorted Array
* Sorted Matrix
* Rotated Sorted Array
* Minimum Possible
* Maximum Possible
* K-th Smallest
* Search Space
* Find First
* Find Last
* Peak Element
* Minimize
* Maximize

Keywords:

```text
Find Minimum

Find Maximum

Search

First

Last

Smallest Valid

Largest Valid
```

---

# Generic Template

```java
int left = 0;
int right = n - 1;

while(left <= right){

    int mid =
        left + (right-left)/2;

    if(nums[mid] == target){
        return mid;
    }

    else if(nums[mid] < target){
        left = mid + 1;
    }

    else{
        right = mid - 1;
    }
}
```

---

# Why Use

```java
left + (right-left)/2
```

instead of:

```java
(left + right)/2
```

Because:

```text
left + right
```

can overflow for large values.

---

# Binary Search Variations

## Variation 1

### Classical Binary Search

Goal:

```text
Find Target
```

Problems:

```text
LC704 Binary Search

LC35 Search Insert Position
```

---

## Variation 2

### First / Last Occurrence

Goal:

```text
Find Boundaries
```

Problems:

```text
LC34 Find First and Last Position

LC278 First Bad Version
```

---

## Variation 3

### Lower Bound / Upper Bound

Goal:

```text
Find Insertion Position
```

Problems:

```text
LC35 Search Insert Position

LC744 Find Smallest Letter Greater Than Target
```

---

## Variation 4

### Rotated Sorted Arrays

Goal:

```text
Search despite rotation
```

Problems:

```text
LC33 Search in Rotated Sorted Array

LC81 Search in Rotated Sorted Array II

LC153 Find Minimum in Rotated Sorted Array
```

---

## Variation 5

### Binary Search on Answer

Goal:

```text
Search Answer Space
```

Most important interview variation.

Problems:

```text
LC875 Koko Eating Bananas

LC1011 Capacity To Ship Packages

LC410 Split Array Largest Sum

LC1482 Minimum Days to Make Bouquets
```

---

## Variation 6

### Peak / Mountain Problems

Goal:

```text
Find Local Maximum
```

Problems:

```text
LC162 Find Peak Element

LC852 Peak Index in Mountain Array

LC1095 Find in Mountain Array
```

---

## Variation 7

### Matrix Binary Search

Goal:

```text
Search in 2D Structures
```

Problems:

```text
LC74 Search a 2D Matrix

LC240 Search a 2D Matrix II
```

---

## Variation 8

### Partition Binary Search

Goal:

```text
Search Partition Boundary
```

Advanced Interview Problems.

Problems:

```text
LC4 Median of Two Sorted Arrays

LC719 K-th Smallest Pair Distance
```

---

# Most Important Variation

For interviews:

```text
Binary Search on Answer
```

is asked far more frequently than classical binary search.

Examples:

```text
Koko Eating Bananas

Ship Packages

Minimum Days

Split Array
```

---

# Common Mistakes

## Mistake 1

Using:

```java
mid = (left + right)/2
```

Risk:

```text
Integer Overflow
```

---

## Mistake 2

Infinite Loop

Wrong:

```java
left = mid;
```

Correct:

```java
left = mid + 1;
```

or

```java
right = mid - 1;
```

---

## Mistake 3

Not Identifying Monotonicity

Before applying Binary Search ask:

```text
Can I divide the search space into:

Invalid Region
Valid Region
```

If yes:

```text
Binary Search is probably possible.
```

---

# Complexity

### Time

```text
O(log N)
```

### Space

```text
O(1)
```

---

# Interview Strategy

Always ask:

```text
What is the search space?

What is the monotonic property?

Can I eliminate half
after each decision?
```

If the answer is yes:

```text
Use Binary Search.
```

---

# One-Line Revision

```text
Binary Search =
Search on a monotonic space by repeatedly eliminating half of the possibilities.
```

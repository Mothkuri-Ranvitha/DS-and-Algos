# Heap / Priority Queue Pattern

---

# What is a Heap?

A Heap is a special tree-based data structure that allows us to quickly access the:

```text
Smallest Element
```

or

```text
Largest Element
```

without sorting the entire data.

---

## Why Do We Need Heap?

Suppose:

```java
nums = [10, 3, 20, 5, 1]
```

Question:

```text
Find Largest Element
```

Without Heap:

```java
Arrays.sort(nums);
```

Complexity:

```text
O(N log N)
```

---

With Heap:

```java
PriorityQueue<Integer>
```

we can access:

```text
Minimum
or
Maximum
```

in:

```text
O(1)
```

and insert/delete in:

```text
O(log N)
```

---

# Heap vs Binary Search Tree

| Operation  | Heap     | BST      |
| ---------- | -------- | -------- |
| Find Min   | O(1)     | O(log N) |
| Find Max   | O(1)     | O(log N) |
| Search     | O(N)     | O(log N) |
| Insert     | O(log N) | O(log N) |
| Delete Top | O(log N) | O(log N) |

---

# Types of Heap

---

## 1. Min Heap

Smallest element stays on top.

Example:

```text
        1
      /   \
     3     5
    / \
   7   8
```

Top:

```java
1
```

---

### Java

```java
PriorityQueue<Integer> pq =
    new PriorityQueue<>();
```

---

Operations

```java
pq.offer(5);

pq.offer(1);

pq.offer(10);

pq.peek();

pq.poll();
```

---

## 2. Max Heap

Largest element stays on top.

Example:

```text
        10
       /  \
      5    3
     /
    1
```

Top:

```java
10
```

---

### Java

```java
PriorityQueue<Integer> pq =
    new PriorityQueue<>(
        Collections.reverseOrder());
```

---

# Heap Complexity

| Operation  | Complexity |
| ---------- | ---------- |
| Peek       | O(1)       |
| Insert     | O(log N)   |
| Delete Top | O(log N)   |
| Build Heap | O(N)       |

---

# When Should You Think About Heap?

Look for these keywords:

```text
Top K

K Largest

K Smallest

K Closest

Highest Priority

Lowest Cost

Stream

Median

Merge K Sorted

Scheduling

Frequency
```

---

# Recognition Signals

### Signal 1

Need only:

```text
Largest Element

Smallest Element
```

not full sorting.

---

### Signal 2

Need:

```text
Top K Elements
```

---

### Signal 3

Continuously arriving data.

```text
Stream
```

---

### Signal 4

Always process:

```text
Highest Priority First
```

---

### Signal 5

Need repeated:

```text
Extract Minimum

Extract Maximum
```

---

# Core Heap Patterns

---

# Variation 1

## Top K Problems

Find:

```text
Top K Largest

Top K Frequent

K Smallest
```

Problems:

```text
LC215 Kth Largest Element

LC347 Top K Frequent Elements
```

---

# Variation 2

## K Closest Problems

Find:

```text
K Closest Elements

K Closest Points
```

Problems:

```text
LC973 K Closest Points

LC658 Find K Closest Elements
```

---

# Variation 3

## Merge K Sorted Structures

Merge multiple sorted structures efficiently.

Problems:

```text
LC23 Merge K Sorted Lists

LC373 Find K Pairs With Smallest Sums
```

---

# Variation 4

## Two Heaps Pattern

Maintain:

```text
Smaller Half

Larger Half
```

using:

```text
Max Heap

Min Heap
```

Problems:

```text
LC295 Find Median From Data Stream

Sliding Window Median
```

---

# Variation 5

## Scheduling Problems

Always process:

```text
Earliest Finish

Highest Priority

Minimum Cost
```

Problems:

```text
LC621 Task Scheduler

LC253 Meeting Rooms II
```

---

# Variation 6

## Greedy + Heap

Choose best available option at every step.

Problems:

```text
LC502 IPO

LC857 Minimum Cost To Hire Workers
```

---

# Variation 7

## Frequency Based Problems

Count frequencies then use heap.

Problems:

```text
LC347 Top K Frequent Elements

LC451 Sort Characters By Frequency

LC692 Top K Frequent Words
```

---

# Decision Tree

Question:

```text
Need full sorting?
```

Yes

↓

```text
Sorting
```

No

↓

Need:

```text
Largest

Smallest

Top K
```

↓

```text
Heap
```

---

# Heap Templates

---

## Min Heap

```java
PriorityQueue<Integer> pq =
    new PriorityQueue<>();
```

---

## Max Heap

```java
PriorityQueue<Integer> pq =
    new PriorityQueue<>(
        Collections.reverseOrder());
```

---

## Custom Comparator

```java
PriorityQueue<int[]> pq =
    new PriorityQueue<>(
        (a,b)->a[0]-b[0]);
```

---

## Top K Largest

```java
PriorityQueue<Integer> pq =
    new PriorityQueue<>();

for(int num : nums){

    pq.offer(num);

    if(pq.size() > k){

        pq.poll();
    }
}
```

---

# Common Mistakes

### Mistake 1

Sorting entire array.

```java
Arrays.sort(nums);
```

when only:

```text
Top K
```

is required.

---

### Mistake 2

Using Max Heap when Min Heap is needed.

---

### Mistake 3

For K Largest:

```text
Maintain Min Heap of size K
```

NOT Max Heap of size N.

---

# Interview Checklist

Whenever you see:

```text
Top K

K Closest

Median

Priority

Scheduling

Stream

Frequency
```

Ask:

```text
Can I keep only the most important
elements using a Heap?
```

If yes:

```text
Heap / Priority Queue Pattern
```

---

# Heap Pattern Roadmap

```text
Heap
│
├── 01 Top K Problems
│     ├── LC215 Kth Largest
│     └── LC347 Top K Frequent
│
├── 02 K Closest Problems
│     ├── LC973 K Closest Points
│     └── LC658 K Closest Elements
│
├── 03 Merge K Sorted
│     ├── LC23 Merge K Lists
│     └── LC373 Smallest Pairs
│
├── 04 Two Heaps Pattern
│     └── LC295 Median Stream
│
├── 05 Scheduling Problems
│     ├── LC621 Task Scheduler
│     └── LC253 Meeting Rooms II
│
├── 06 Greedy + Heap
│     ├── LC502 IPO
│     └── LC857 Hire Workers
│
└── 07 Frequency Problems
      ├── LC347
      ├── LC451
      └── LC692
```

---

# One-Line Revision

```text
Heap =
When you repeatedly need the
smallest, largest, or Top-K elements
without sorting everything.
```

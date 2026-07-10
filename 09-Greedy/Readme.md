# Greedy Pattern - README.md

---

# What is Greedy?

A **Greedy Algorithm** makes the **best possible decision at the current moment** without considering future consequences.

Instead of exploring every possible choice (like Backtracking) or comparing all possibilities (like Dynamic Programming), Greedy believes that:

> **A sequence of locally optimal choices will lead to a globally optimal solution.**

---

## Real Life Analogy

Suppose you're walking to college.

There are several roads.

Instead of checking every possible route, you always choose the road that **looks shortest right now**.

```text
Current Best Choice
        ↓
Current Best Choice
        ↓
Current Best Choice
        ↓
Final Answer
```

This is Greedy thinking.

---

# Core Intuition

Greedy solves problems by answering one question repeatedly:

```text
"What is the best decision I can make right now?"
```

Once a decision is made,

```text
It is NEVER changed again.
```

Unlike Dynamic Programming,

Greedy **does not backtrack**.

---

# Example

Suppose:

```text
Coins:

10

5

2

1

Amount = 18
```

Greedy picks

```text
10
```

Remaining

```text
8
```

Then picks

```text
5
```

Remaining

```text
3
```

Then

```text
2
```

Remaining

```text
1
```

Then

```text
1
```

Finished.

Greedy never asks:

> "Should I have picked another coin?"

It simply trusts that the current best choice leads to the optimal answer.

---

# Recognition Signals

Whenever you see:

* Maximum Profit
* Minimum Cost
* Minimum Number
* Maximum Number
* Fewest Operations
* Reach End
* Merge Intervals
* Scheduling
* Assign Jobs
* Activity Selection
* Choose K Items

Think:

```text
Can a local best decision solve this?
```

---

# When Does Greedy Work?

Greedy works only when **both** of these properties exist.

## 1. Greedy Choice Property

Making the best local decision should never prevent the optimal solution later.

Example:

```text
Jump Game

Always jump to the farthest reachable position.
```

---

## 2. Optimal Substructure

After making one decision,

the remaining problem should still be an optimal problem of the same type.

---

# When Greedy Fails

Sometimes the locally best decision produces a bad overall result.

Example:

```text
Coins:

4

3

1

Amount = 6
```

Greedy:

```text
4

1

1
```

3 coins.

Optimal:

```text
3

3
```

2 coins.

So Greedy fails.

Dynamic Programming is needed.

---

# Greedy vs Dynamic Programming

| Greedy                   | Dynamic Programming                                    |
| ------------------------ | ------------------------------------------------------ |
| Makes local best choice  | Considers all possibilities                            |
| Never revisits decisions | Revisits previous states                               |
| Faster                   | Usually slower                                         |
| Easier implementation    | More complex                                           |
| Doesn't always work      | Always finds optimal solution (when modeled correctly) |

---

# Common Greedy Techniques

## 1. Local Best Decision

Choose the best available option immediately.

Examples:

* Jump Game
* Assign Cookies

---

## 2. Sorting + Greedy

Sort first.

Then make greedy decisions.

Examples:

* Merge Intervals
* Minimum Arrows
* Boats to Save People

---

## 3. Interval Scheduling

Sort intervals.

Choose compatible intervals.

Examples:

* Non-overlapping Intervals
* Meeting Rooms

---

## 4. Resource Allocation

Limited resources.

Choose the most beneficial option.

Examples:

* Maximum Units on Truck
* IPO

---

## 5. Reachability

Maintain the farthest reachable position.

Examples:

* Jump Game
* Jump Game II

---

## 6. String Greedy

Build the answer character by character.

Examples:

* Partition Labels
* Remove Duplicate Letters

---

## 7. Heap + Greedy

Always choose the currently best resource using a Priority Queue.

Examples:

* IPO
* Furthest Building
* Hire Workers

---

# Complete Variation Roadmap

```
Greedy
│
├── 01 Local Greedy Decisions
│
├── 02 Interval Greedy
│
├── 03 Scheduling
│
├── 04 Resource Allocation
│
├── 05 Reachability
│
├── 06 String Greedy
│
├── 07 Heap + Greedy
│
└── 08 Advanced Greedy
```

---

# Interview Recognition Flow

```text
Need Optimal Answer?

        │
        ▼

Can I make the best decision RIGHT NOW?

        │

       YES
        │

Will this decision NEVER need to change?

        │

       YES
        │

Does choosing locally still produce
the global optimum?

        │

       YES
        │

Use Greedy
```

---

# Common Interview Questions

### Beginner

* LC455 Assign Cookies
* LC605 Can Place Flowers
* LC860 Lemonade Change

---

### Intermediate

* LC55 Jump Game
* LC45 Jump Game II
* LC763 Partition Labels
* LC881 Boats to Save People
* LC452 Minimum Number of Arrows

---

### Advanced

* LC134 Gas Station
* LC135 Candy
* LC621 Task Scheduler
* LC502 IPO
* LC630 Course Schedule III

---

# Complexity

Greedy algorithms are usually:

```text
Sorting Based

Time : O(N log N)
```

or

```text
Single Scan

Time : O(N)
```

Space is often:

```text
O(1)

or

O(N)
```

depending on the problem.

---

# Pattern Checklist

Before solving a problem, ask yourself:

✅ Can I make the best decision now?

✅ Will I ever need to change that decision later?

✅ Does the problem ask for minimum/maximum/fewest/most?

✅ Can sorting simplify the decisions?

If the answer is "Yes" to most of these questions,

Greedy is a strong candidate.

---

# One-Line Revision

```text
Greedy =
Choose the best decision available now,
never reconsider it,
and trust that local optimum leads to global optimum.
```

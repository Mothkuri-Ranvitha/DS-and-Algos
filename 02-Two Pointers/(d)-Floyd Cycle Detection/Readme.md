# Floyd Cycle Detection (Fast & Slow Pointers)

> If a cycle exists, fast will eventually catch slow.

---

## Why Does This Pattern Exist?

Many problems involve:

* Linked Lists
* Cycles
* Loops
* Circular Traversal
* Duplicate Detection

Using a HashSet works:

```text
Time  : O(N)

Space : O(N)
```

But interviewers often ask:

```text
Can you solve it in O(1) space?
```

Floyd's Algorithm does exactly that.

---

## Core Intuition

Two pointers move at different speeds.

```text
Slow = 1 step

Fast = 2 steps
```

Visual:

```text
Slow → ● → ● → ●

Fast → ● → ● → ● → ●
```

If a cycle exists:

```text
Fast eventually catches Slow
```

just like a faster runner catches a slower runner on a circular track.

---

## Recognition Signals

Think Floyd Cycle Detection when you see:

* Linked List Cycle
* Circular Array
* Loop Detection
* Duplicate Number
* Happy Number
* O(1) Space Requirement

---

## Generic Template

```java
ListNode slow = head;
ListNode fast = head;

while(fast != null &&
      fast.next != null) {

    slow = slow.next;
    fast = fast.next.next;

    if(slow == fast)
        return true;
}

return false;
```

---

# Example Problems

## LC141 - Linked List Cycle

### Goal

Detect whether a cycle exists.

Example:

```text
1 → 2 → 3 → 4
      ↑     ↓
      ← ← ←
```

### Code

```java
public boolean hasCycle(ListNode head) {

    ListNode slow = head;
    ListNode fast = head;

    while(fast != null &&
          fast.next != null) {

        slow = slow.next;
        fast = fast.next.next;

        if(slow == fast)
            return true;
    }

    return false;
}
```

Time: O(N)

Space: O(1)

---

## LC142 - Linked List Cycle II

### Goal

Find starting node of cycle.

Example:

```text
1 → 2 → 3 → 4
      ↑     ↓
      ← ← ←
```

Answer:

```text
Node 2
```

### Key Idea

After collision:

```text
Move one pointer to head.
```

Then move both one step.

Meeting point = cycle start.

Time: O(N)

Space: O(1)

---

## LC287 - Find Duplicate Number

### Goal

Find duplicate without modifying array.

Example:

```text
[1,3,4,2,2]

Answer = 2
```

### Observation

Treat values as pointers.

```text
index → value → next index
```

A duplicate creates a cycle.

### Code

```java
class Solution {

    public int findDuplicate(int[] nums) {

        int slow = nums[0];
        int fast = nums[0];

        do {

            slow = nums[slow];

            fast =
                nums[nums[fast]];

        } while(slow != fast);

        slow = nums[0];

        while(slow != fast) {

            slow = nums[slow];
            fast = nums[fast];
        }

        return slow;
    }
}
```

Time: O(N)

Space: O(1)

---

## LC202 - Happy Number

### Goal

Detect repeating sequence.

Example:

```text
19

↓

82

↓

68

↓

100

↓

1
```

or

```text
4

↓

16

↓

37

↓

58

↓

89

↓

145

↓

42

↓

20

↓

4
```

Cycle appears.

Use Floyd detection.

Time: O(logN)

Space: O(1)

---

# Learning Order

```text
LC141
   ↓
LC142
   ↓
LC202
   ↓
LC287
```

---

# Pattern Tracker

```text
Pattern:
Floyd Cycle Detection

Core Idea:
Fast moves 2 steps
Slow moves 1 step

Recognition:
Cycle
Loop
Duplicate
Circular Traversal

Goal:
Detect cycles using O(1) space
```

---

# Complexity

```text
Time  : O(N)

Space : O(1)
```

---

# One-Line Revision

```text
Fast catches Slow
⇒ Cycle Exists
```

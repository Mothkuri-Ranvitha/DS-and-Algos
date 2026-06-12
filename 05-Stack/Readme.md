# Stack

> A Stack remembers the most recent unfinished work.

---

# Definition

A Stack is a linear data structure that follows the **LIFO** principle:

```text
Last In
First Out
```

The last element inserted is the first element removed.

Visual:

```text
Push(1)

1

Push(2)

2
1

Push(3)

3
2
1

Pop()

2
1
```

The most recent item always stays on top.

---

# Why Does This Pattern Exist?

Many problems require us to remember something temporarily and process it later.

Examples:

```text
Open Parentheses

(
```

We must remember it until:

```text
)
```

appears.

---

```text
Browser History

Google
↓
YouTube
↓
GitHub
```

When user clicks Back:

```text
GitHub removed first
```

Most recent page comes out first.

---

```text
Function Calls

main()
 ↓
funA()
 ↓
funB()
```

When funB finishes:

```text
Return to funA
```

Stack manages this automatically.

---

Without Stack:

```text
Remembering unfinished work
becomes difficult.
```

---

# Core Intuition

The key question is:

```text
What am I waiting for?
```

If the answer is:

```text
I need to remember something
until a matching event appears
```

Think:

```text
STACK
```

---

Example:

```text
( [ { } ] )
```

When reading:

```text
(
```

we are waiting for:

```text
)
```

Stack remembers it.

---

# Real Life Analogies

## Plate Stack

```text
Plate 1
Plate 2
Plate 3
```

Removing:

```text
Plate 3 first
```

LIFO.

---

## Undo Operation

```text
Write A
Write B
Write C
```

Undo:

```text
Remove C
```

Most recent operation removed first.

---

## Browser Back Button

```text
Amazon
↓
YouTube
↓
GitHub
```

Back:

```text
GitHub removed
```

Most recent page leaves first.

---

# Recognition Signals

Think Stack when you see:

### Matching Pairs

```text
()
[]
{}
<>
```

---

### Undo Operations

```text
Backspace

Undo

History
```

---

### Most Recent Element Matters

```text
Nearest Previous

Latest Action

Recent Operation
```

---

### Nested Structures

```text
((()))

[a(b)c]

3[a2[c]]
```

---

### Expression Evaluation

```text
2 + 3

Postfix

Prefix
```

---

# Mental Model

Whenever you read a problem ask:

### Question 1

```text
Do I need to remember
something temporarily?
```

If YES:

```text
Think Stack
```

---

### Question 2

```text
Will I process
the most recent item first?
```

If YES:

```text
Think Stack
```

---

### Question 3

```text
Am I matching pairs?
```

If YES:

```text
Think Stack
```

---

### Question 4

```text
Am I handling nested structures?
```

If YES:

```text
Think Stack
```

---

# Basic Operations

## Push

Insert element.

```java
stack.push(x);
```

---

## Pop

Remove top element.

```java
stack.pop();
```

---

## Peek

View top element.

```java
stack.peek();
```

---

## Empty

Check stack empty.

```java
stack.isEmpty();
```

---

# Generic Template

```java
Stack<Integer> stack =
        new Stack<>();

for(int num : nums){

    // process

    stack.push(num);
}
```

---

# Important Observations

## Observation 1

Stack processes items in reverse order.

Example:

```text
Input:

1 2 3

Stack:

3
2
1
```

---

## Observation 2

Stack is excellent for matching problems.

Example:

```text
(
[
{
```

Store openings.

Match when closing appears.

---

## Observation 3

Nested structures often indicate Stack.

Example:

```text
3[a2[c]]
```

Need to remember previous state.

---

## Observation 4

Recursion internally uses Stack.

```text
main()
 ↓
A()
 ↓
B()
```

Call stack handles returns.

---

# Common Mistakes

## Mistake 1

Using Stack when Queue is needed.

Stack:

```text
LIFO
```

Queue:

```text
FIFO
```

Always identify order first.

---

## Mistake 2

Forgetting Empty Check

Wrong:

```java
stack.peek();
```

when stack empty.

Always verify:

```java
if(!stack.isEmpty())
```

---

## Mistake 3

Pushing unnecessary information.

Store only information required later.

---

# Major Variations

## 1. Balanced Parentheses

Goal:

```text
Match opening and closing brackets.
```

Examples:

```text
LC20 Valid Parentheses

LC921 Minimum Add to Make Parentheses Valid
```

---

## 2. Expression Evaluation

Goal:

```text
Evaluate mathematical expressions.
```

Examples:

```text
LC150 Reverse Polish Notation
```

---

## 3. Stack Simulation

Goal:

```text
Undo operations
History tracking
Previous actions
```

Examples:

```text
LC682 Baseball Game

LC844 Backspace String Compare
```

---

## 4. Min Stack

Goal:

```text
Get minimum quickly.
```

Examples:

```text
LC155 Min Stack
```

---

## 5. String Manipulation Using Stack

Goal:

```text
Remove characters

Decode strings

Handle nested strings
```

Examples:

```text
LC1047 Remove Adjacent Duplicates

LC394 Decode String
```

---

# Problem Roadmap

## Foundation

```text
LC20 Valid Parentheses

LC1047 Remove Adjacent Duplicates
```

---

## Intermediate

```text
LC682 Baseball Game

LC155 Min Stack
```

---

## Advanced

```text
LC150 Reverse Polish Notation

LC394 Decode String
```

---

# Interview Explanation

"Stack is useful when the most recently seen element must be processed first. It naturally handles matching pairs, nested structures, undo operations, and expression evaluation through its LIFO behavior."

---

# Revision Sheet

## Recognition Signals

```text
Matching Pairs

Undo

History

Nested Structures

Most Recent Element
```

---

## Core Idea

```text
Remember unfinished work.
```

---

## Major Variations

```text
Balanced Parentheses

Expression Evaluation

Stack Simulation

Min Stack

String Manipulation
```

---

## Complexity

Push:

```text
O(1)
```

Pop:

```text
O(1)
```

Peek:

```text
O(1)
```

Space:

```text
O(N)
```

---

# Pattern Tracker

```text
Pattern:
Stack

Core Idea:
Remember recent unfinished work

Recognition:
Matching
Undo
Nested Structures

Goal:
Process most recent item first

Order:
LIFO
```

---

# One-Line Revision

```text
Stack =
The most recently unfinished work gets completed first.
```

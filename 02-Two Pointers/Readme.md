# Pattern #2: Two Pointers

> "Don't search everywhere. Eliminate impossible answers."

---

## Why Does This Pattern Exist?

Brute force for most array/string problems is:

```
Try every possibility → O(N²)
```

Two Pointers lets you **eliminate large chunks of the search space** without checking them.

```
O(N²)  →  O(N)
```

That single shift is why this pattern shows up in nearly every interview.

---

## The Core Idea

Think of two pointers as two detectives searching strategically.

Instead of checking every pair:

```
[1, 2, 3, 4, 5, 6, 7, 8]   Target = 9

Brute: 1+2, 1+3, 1+4 ... 7+8   → O(N²)

Two Pointers:
L=1, R=8 → sum=9 ✓ Found.
Done in one step.
```

We move pointers **based on logic**, not random checking.

---

## The Golden Question

When you see a new problem, ask yourself:

```
Can I move pointers intelligently
instead of checking everything?
```

If yes → Think Two Pointers.

---

## Recognition Signals

**Arrays:**
- Sorted array + pair/triplet problems
- In-place modification
- Remove duplicates / elements
- Move elements around

**Strings:**
- Palindrome check
- Reverse operations
- Substring problems

**Linked Lists:**
- Cycle detection
- Middle node
- Fast-slow movement

---

## The Two Pointers Family

> Most people think Two Pointers is one pattern. It's not. It contains 4 distinct patterns.

```
Two Pointers
│
├── (a) Opposite Direction Pointers    ← Start from both ends, move inward
│
├── (b) Same Direction Pointers
│       ├── Fast-Slow Pointer          ← Fast reads, slow writes
│       └── Read-Write Pointer         ← Mental separation for clarity
│
├── (c) Sliding Window
│       ├── Fixed Window               ← Window size never changes
│       └── Variable Window            ← Expand and shrink based on condition
│
└── (d) Floyd Cycle Detection          ← Slow 1 step, Fast 2 steps
```

---

## (a) Opposite Direction Pointers

Pointers start from opposite ends and move inward.

```
L                   R
[1  2  3  4  5  6  7]
 ↑                 ↑
```

**Mental model:** Search space elimination.

**When to use:**
- Sorted array + pair sum
- Palindrome check
- Reverse operations
- Anything comparing from both ends

**Problems:**

| Problem | Difficulty | Variation |
|---------|------------|-----------|
| LC125 Valid Palindrome | Easy | Basic palindrome |
| LC344 Reverse String | Easy | Basic reverse |
| LC167 Two Sum II | Medium | Pair sum sorted |
| LC977 Squares of Sorted Array | Easy | Squares + sort |
| LC11 Container With Most Water | Medium | Maximize area |
| LC15 3Sum | Medium | Fix one + two pointers |
| LC16 3Sum Closest | Medium | Closest target |
| LC18 4Sum | Medium | Fix two + two pointers |
| LC42 Trapping Rain Water | Hard | Max tracking both sides |

---

## (b) Same Direction Pointers

Both pointers move left → right, but at different roles.

```
S
F
0  1  2  3  4  5  6

       S
             F
```

**Mental model:** One pointer reads, one pointer maintains.

**When to use:**
- Remove duplicates
- Remove elements
- Move zeroes
- In-place array compaction

**Problems:**

| Problem | Difficulty |
|---------|------------|
| LC26 Remove Duplicates from Sorted Array | Easy |
| LC27 Remove Element | Easy |
| LC283 Move Zeroes | Easy |
| LC905 Sort Array By Parity | Easy |
| LC443 String Compression | Medium |

---

## (c) Sliding Window

Evolved from Two Pointers. Treat it as its own sub-pattern.

**Core idea:** Maintain a window `[L........R]` instead of rebuilding from scratch.

### Fixed Window

Window size never changes.

```
[1  2  3]  4  5
1  [2  3  4]  5
1  2  [3  4  5]
```

**Problems:**

| Problem | Difficulty |
|---------|------------|
| LC643 Maximum Average Subarray I | Easy |
| LC1456 Maximum Number of Vowels in a Substring | Medium |
| LC1343 Number of Subarrays of Size K and Average ≥ Threshold | Medium |

### Variable Window

Window expands and shrinks.

```
Expand →

[L.......R]

Condition breaks → Shrink ←
```

**Problems:**

| Problem | Difficulty |
|---------|------------|
| LC209 Minimum Size Subarray Sum | Medium |
| LC3 Longest Substring Without Repeating Characters | Medium |
| LC424 Longest Repeating Character Replacement | Medium |
| LC1004 Max Consecutive Ones III | Medium |
| LC76 Minimum Window Substring | Hard |

---

## (d) Floyd Cycle Detection

Special fast-slow pointer pattern. Fast takes 2 steps, slow takes 1.

```
If a cycle exists → Fast eventually catches Slow.
```

**Problems:**

| Problem | Difficulty |
|---------|------------|
| LC141 Linked List Cycle | Easy |
| LC142 Linked List Cycle II | Medium |
| LC287 Find the Duplicate Number | Medium |
| LC202 Happy Number | Easy |

---

## Learning Order

> **Do not jump to Sliding Window first.**
> The intuition for window movement comes from mastering pointer movement in (a) and (b).

```
Step 1: Opposite Direction
       ↓
Step 2: Same Direction
       ↓
Step 3: Fixed Sliding Window
       ↓
Step 4: Variable Sliding Window
       ↓
Step 5: Floyd Cycle Detection
```

---

## Repository Structure

```
02-Two-Pointers/
│
├── README.md                         ← You are here
│
├── (a)-Opposite-Direction-Pointers/
│       ├── README.md
│       ├── LC125-Valid-Palindrome/
│       ├── LC344-Reverse-String/
│       ├── LC167-Two-Sum-II/
│       ├── LC977-Squares-Sorted-Array/
│       ├── LC11-Container-With-Most-Water/
│       ├── LC15-3Sum/
│       └── LC42-Trapping-Rain-Water/
│
├── (b)-Same-Direction-Pointers/
│       ├── Fast-Slow/
│       │       ├── LC26/
│       │       ├── LC27/
│       │       └── LC283/
│       └── Read-Write/
│               └── LC443/
│
├── (c)-Sliding-Window/
│       ├── Fixed/
│       │       ├── LC643/
│       │       └── LC1456/
│       └── Variable/
│               ├── LC209/
│               ├── LC3/
│               ├── LC424/
│               └── LC76/
│
└── (d)-Floyd-Cycle-Detection/
        ├── LC141/
        ├── LC142/
        └── LC287/
```

---

## Pattern Tracker

| Field | Value |
|-------|-------|
| Pattern | Two Pointers |
| Core Idea | Move pointers intelligently instead of checking everything |
| Goal | Reduce O(N²) to O(N) |
| Key Signal | Sorted array, pair sum, palindrome, in-place modification, window |

---

## One-Line Revision

```
Two Pointers is the art of eliminating impossible answers without checking them.
```

---

## Challenge Goal

After completing this pattern, you should be able to:

- Recognize Opposite / Same / Fixed Window / Variable Window / Floyd within **30 seconds** of reading a problem.
- Know **why** you're picking a specific sub-pattern, not just that it "looks like two pointers."

That is the real objective.

---

**Next →** `(a)-Opposite-Direction-Pointers/README.md`
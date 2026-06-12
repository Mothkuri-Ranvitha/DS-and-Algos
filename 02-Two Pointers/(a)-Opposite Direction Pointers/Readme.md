# (a) Opposite Direction Pointers

> "Start from both ends. Move inward. Eliminate what's impossible."

---

## What Is This Pattern?

Two pointers start at **opposite ends** of the array or string.

They move **toward each other** until they meet or cross.

```
L                   R
[1  2  3  4  5  6  7]
 ↑                 ↑
        move inward
        ↓         ↓
```

Every step eliminates impossible candidates.

---

## Why It Works

When an array is sorted (or can be sorted), we know:

- Everything to the right of L is **larger**
- Everything to the left of R is **smaller**

So if `L + R > target`:  
→ R is too big. Move R left.

If `L + R < target`:  
→ L is too small. Move L right.

No need to check every combination.

---

## Template

```java
int left = 0, right = nums.length - 1;

while (left < right) {
    int current = process(nums[left], nums[right]);

    if (current == target) {
        // found answer
        return result;
    } else if (current < target) {
        left++;   // need something bigger
    } else {
        right--;  // need something smaller
    }
}
```

This template applies to **all variations** in this folder.  
The only thing that changes is the `process()` logic and the condition.

---

## Recognition Signals

Use Opposite Direction Pointers when you see:

```
✓ Sorted array (or sorting is acceptable)
✓ Find a pair / triplet / subset
✓ Palindrome check
✓ Reverse something in-place
✓ Maximize or minimize something involving two elements
✓ Brute force is O(N²) and N ≤ 10⁵
```

Keywords to look for:
```
pair    sum    target    palindrome    sorted    reverse
closest    two numbers    container    water    k-sum
```

---

## The Variations Map

```
Opposite Direction Pointers
│
├── Variation 1: Palindrome Check
│       → Compare chars from both ends
│       → LC125, LC680
│
├── Variation 2: Reverse Array / String
│       → Swap from both ends, move inward
│       → LC344, LC345
│
├── Variation 3: Pair Sum (Sorted)
│       → Classic two sum on sorted input
│       → LC167, LC977
│
├── Variation 4: Maximize / Minimize Area
│       → Move the shorter side, not the taller
│       → LC11
│
├── Variation 5: K-Sum (3Sum, 4Sum)
│       → Fix outer element(s), run two pointers inside
│       → LC15, LC16, LC18, LC259
│
└── Variation 6: Trapping Rain Water
        → Track max from both sides, process smaller side first
        → LC42
```

---

## Variation 1: Palindrome Check

### Core Idea

Compare characters from both ends.  
Move inward only when characters match.  
Stop when they don't.

```
s = "racecar"

L=0  R=6 → r == r ✓ → move
L=1  R=5 → a == a ✓ → move
L=2  R=4 → c == c ✓ → move
L=3 == R=3 → done → it's a palindrome
```

### When to Use
- Is this string a palindrome?
- Can we make it a palindrome with one deletion?
- Is this numeric value a palindrome?

### Problems

| LC | Title | Difficulty | Key Twist |
|----|-------|------------|-----------|
| LC125 | Valid Palindrome | Easy | Skip non-alphanumeric |
| LC680 | Valid Palindrome II | Medium | Allow one deletion |
| LC9 | Palindrome Number | Easy | Without converting to string |
| LC5 | Longest Palindromic Substring | Medium | Expand from center instead |

### Common Mistake

LC125 has non-alphanumeric characters.  
The fix: skip them inside the loop.

```java
while (left < right) {
    while (left < right && !Character.isLetterOrDigit(s.charAt(left)))  left++;
    while (left < right && !Character.isLetterOrDigit(s.charAt(right))) right--;

    if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right)))
        return false;

    left++;
    right--;
}
return true;
```

---

## Variation 2: Reverse Array / String

### Core Idea

Swap elements from both ends.  
Move inward after each swap.

```
[1, 2, 3, 4, 5]
 L           R

Step 1: swap(1,5) → [5, 2, 3, 4, 1]
Step 2: swap(2,4) → [5, 4, 3, 2, 1]
L meets R → done
```

### When to Use
- Reverse an array in-place
- Reverse vowels only
- Reverse words in a sentence (reverse whole, then each word)

### Problems

| LC | Title | Difficulty | Key Twist |
|----|-------|------------|-----------|
| LC344 | Reverse String | Easy | Pure swap |
| LC345 | Reverse Vowels of a String | Easy | Only swap vowels, skip consonants |
| LC151 | Reverse Words in a String | Medium | Reverse whole → reverse each word |

---

## Variation 3: Pair Sum on Sorted Array

### Core Idea

```
If sum < target  →  move left pointer right (need larger)
If sum > target  →  move right pointer left (need smaller)
If sum == target →  found
```

### Why Sorting Matters

Without sorting, you can't decide which pointer to move.  
Sorted input gives us the **direction of the answer**.

### Problems

| LC | Title | Difficulty | Key Twist |
|----|-------|------------|-----------|
| LC167 | Two Sum II | Medium | Direct pair sum |
| LC977 | Squares of Sorted Array | Easy | Squares — largest at edges |

### LC977 Insight

After squaring, the largest values are at the **ends** (most negative or most positive).  
Use two pointers and fill result array from right to left.

```java
int[] result = new int[n];
int pos = n - 1;

while (left <= right) {
    if (Math.abs(nums[left]) > Math.abs(nums[right])) {
        result[pos--] = nums[left] * nums[left];
        left++;
    } else {
        result[pos--] = nums[right] * nums[right];
        right--;
    }
}
```

---

## Variation 4: Maximize / Minimize Area

### Problem: LC11 — Container With Most Water

You have heights. Find two lines that hold the most water.

```
Area = min(height[L], height[R]) × (R - L)
```

### Key Insight

Move the **shorter** height pointer inward.

Why?

If we move the taller one, the width shrinks AND height can only stay same or get worse.  
If we move the shorter one, width shrinks but height might improve.

```
Always move the pointer with the smaller height.
```

### Template

```java
int left = 0, right = heights.length - 1;
int maxArea = 0;

while (left < right) {
    int area = Math.min(heights[left], heights[right]) * (right - left);
    maxArea = Math.max(maxArea, area);

    if (heights[left] < heights[right]) {
        left++;
    } else {
        right--;
    }
}
return maxArea;
```

---

## Variation 5: K-Sum (3Sum, 4Sum)

### Core Idea

Fix the outer element(s). Run two pointers on the rest.

```
3Sum:
- Fix one element at index i
- Run two pointers on [i+1 ... n-1]
- Total: O(N²)

4Sum:
- Fix two elements at indices i, j
- Run two pointers on [j+1 ... n-1]
- Total: O(N³)
```

### Duplicate Handling (Critical)

Sort first. Skip duplicates by checking:
```java
if (i > 0 && nums[i] == nums[i-1]) continue;
```

And inside the two-pointer loop:
```java
while (left < right && nums[left] == nums[left-1]) left++;
while (left < right && nums[right] == nums[right+1]) right--;
```

### Problems

| LC | Title | Difficulty | Key Twist |
|----|-------|------------|-----------|
| LC15 | 3Sum | Medium | Triplets summing to 0, no duplicates |
| LC16 | 3Sum Closest | Medium | Find sum closest to target |
| LC18 | 4Sum | Medium | Fix 2, run 2-pointer |
| LC259 | 3Sum Smaller | Medium | Count triplets with sum < target |
| LC611 | Valid Triangle Number | Medium | Count valid triangles |

### LC16 Twist (3Sum Closest)

Instead of checking `== target`, track the minimum absolute difference.

```java
int closest = nums[0] + nums[1] + nums[2];

for (int i = 0; i < n - 2; i++) {
    int left = i + 1, right = n - 1;
    while (left < right) {
        int sum = nums[i] + nums[left] + nums[right];
        if (Math.abs(sum - target) < Math.abs(closest - target))
            closest = sum;
        if (sum < target) left++;
        else right--;
    }
}
return closest;
```

---

## Variation 6: Trapping Rain Water

### Problem: LC42

Water trapped at position `i` = `min(maxLeft, maxRight) - height[i]`

### Two Pointer Approach

Instead of pre-computing left/right max arrays (O(N) space), use two pointers with running max (O(1) space).

**Key Insight:**

If `height[left] < height[right]`:  
→ The left side controls. Process left pointer.  
→ Water at left = `leftMax - height[left]`

If `height[right] <= height[left]`:  
→ The right side controls. Process right pointer.

```java
int left = 0, right = n - 1;
int leftMax = 0, rightMax = 0, water = 0;

while (left < right) {
    if (height[left] < height[right]) {
        if (height[left] >= leftMax) leftMax = height[left];
        else water += leftMax - height[left];
        left++;
    } else {
        if (height[right] >= rightMax) rightMax = height[right];
        else water += rightMax - height[right];
        right--;
    }
}
return water;
```

### Why This Is Opposite Direction

Water at any position depends on both sides.  
The pointer we process is determined by which side gives the **guaranteed** water level.  
This is the purest form of search space elimination.

---

## All Problems in This Folder

### Ordered by Solving Sequence

```
WEEK 1 — Build the base intuition

LC344   Reverse String              ← Pure swap, simplest possible
LC125   Valid Palindrome            ← First real two-pointer problem
LC680   Valid Palindrome II         ← Add one deletion decision
LC167   Two Sum II                  ← Classic pair sum
LC977   Squares of Sorted Array     ← Fill from back

WEEK 2 — Push further

LC11    Container With Most Water   ← Greedy: move shorter side
LC15    3Sum                        ← Fix one + two pointer
LC16    3Sum Closest                ← Track min difference
LC18    4Sum                        ← Fix two + two pointer

WEEK 3 — Advanced

LC42    Trapping Rain Water         ← Two pointers + running max
LC259   3Sum Smaller                ← Count pairs, not find them
LC611   Valid Triangle Number       ← Triangle inequality variant
```

---

## Complexity Reference

| Variation | Time | Space |
|-----------|------|-------|
| Palindrome Check | O(N) | O(1) |
| Reverse | O(N) | O(1) |
| Pair Sum | O(N) | O(1) |
| 3Sum | O(N²) | O(1) |
| 4Sum | O(N³) | O(1) |
| Container Water | O(N) | O(1) |
| Trapping Rain Water | O(N) | O(1) |

---

## Common Mistakes

### Mistake 1: Not Sorting First

Two pointers only work when array is sorted (for pair/triplet problems).  
Sort before applying.

### Mistake 2: Duplicate Handling in K-Sum

If you don't skip duplicates, you'll get duplicate triplets in the output.  
Always skip: `if (i > 0 && nums[i] == nums[i-1]) continue;`

### Mistake 3: Moving Wrong Pointer in Container Water

Never move the **taller** side. That can only make things worse.  
Always move the **shorter** side.

### Mistake 4: Using `left <= right` vs `left < right`

For pair problems: use `left < right` (pointers shouldn't cross).  
For palindrome problems: use `left < right` (middle element doesn't need checking).

---

## Interview Explanation Template

> "I'll use two pointers starting from opposite ends. Since the array is sorted, I can decide which pointer to move based on whether the current result is too large or too small. This eliminates impossible candidates without checking them and gives O(N) time with O(1) space."

---

## Pattern Tracker

| Field | Value |
|-------|-------|
| Pattern | Opposite Direction Pointers |
| Core Idea | Start from both ends, eliminate search space by moving inward |
| Key Signal | Sorted array, pair/triplet, palindrome, reverse, maximize/minimize |
| Template | `while (left < right)` + condition-based pointer movement |

---

## One-Line Revision

```
When the array is sorted, the answer to "which pointer to move" 
is always: move the one that can't improve the current result.
```

---

**Start here →** `LC344-Reverse-String/`

**Then →** `LC125-Valid-Palindrome/`
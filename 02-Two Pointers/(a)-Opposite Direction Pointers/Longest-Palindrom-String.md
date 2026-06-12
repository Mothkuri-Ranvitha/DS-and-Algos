# LC5 — Longest Palindromic Substring

**Difficulty:** Medium
**Pattern:** Expand From Center
**Variation:** Palindrome Check (1C — Center Expansion)

---

## Problem Statement

Given a string `s`, return the longest palindromic substring in `s`.

```
Input:  s = "babad"
Output: "bab"   (or "aba" — both are valid)

Input:  s = "cbbd"
Output: "bb"
```

---

## Why This Problem Exists

LC125 taught:
```
Check if a string is a palindrome
→ Start from both ends, compare inward
```

LC5 teaches:
```
Find the longest palindrome inside a string
→ You don't know where it starts or ends
→ You must search for it
```

This is an important shift:

| LC125 | LC5 |
|-------|-----|
| Fixed start and end | Unknown start and end |
| Verify a palindrome | Find a palindrome |
| Opposite direction pointers | Expand from center |

---

## First Thought

You might think:

```
Check every possible substring → is it a palindrome?
```

That is O(N³). Too slow.

Better observation:

```
Every palindrome has a center.
If I plant myself at every possible center
and expand outward while characters match,
I find every palindrome efficiently.
```

---

## Why Opposite Direction Pointers Don't Work Here

In LC125 you knew the endpoints. You started there.

In LC5 you don't know where the palindrome is.

```
s = "babad"

Palindrome could start at 0, 1, 2, 3, 4.
No way to start two pointers from the outside.
```

Instead: **grow from the inside out**.

---

## Core Insight

Every palindrome looks like this from the center:

```
Odd length:       b a b a d
                    ↑
                  center = single character

Even length:      a b b a
                   ↑↑
                  center = two characters
```

So for every index `i`, we check two things:

```
1. Treat i alone as center       → odd  length palindrome
2. Treat i and i+1 as center     → even length palindrome
```

Expand L and R outward while `s[L] == s[R]`.
Track the longest window found.

---

## Visual

```
s = "b a b a d"
     0 1 2 3 4

i=2, odd case:
  Step 1: L=2 R=2   →  "b"         match (single char always matches)
  Step 2: L=1 R=3   →  a == a ✓    expand
  Step 3: L=0 R=4   →  b != d ✗    stop

  Palindrome found: s[1..3] = "aba"    length = 3

i=1, odd case:
  Step 1: L=1 R=1   →  "a"
  Step 2: L=0 R=2   →  b == b ✓    expand
  Step 3: L=-1      →  out of bounds, stop

  Palindrome found: s[0..2] = "bab"    length = 3
```

Both "bab" and "aba" are valid answers. Length is 3 either way.

---

## The Golden Formula

After the expand loop exits, L and R have gone **one step too far**:

```
Last valid state:  L=0,  R=2   → both matched
Loop exits at:     L=-1, R=3   → one step beyond

Length = R - L - 1
       = 3 - (-1) - 1
       = 3   ✓
```

This formula works every time because the loop always overshoots by one on each side.

---

## Mental Model

```
For every index i:
    ↓
Plant L and R at center
    ↓
Expand while s[L] == s[R]
    ↓
Record length = R - L - 1
    ↓
Update best if longer
    ↓
Move to next index
```

---

## How To Solve

**Step 1** — Loop over every index as a potential center.

**Step 2** — Call `expand(s, i, i)` for odd-length case.

**Step 3** — Call `expand(s, i, i+1)` for even-length case.

**Step 4** — Take the max of both.

**Step 5** — If longer than current best, update start index and max length.

**Step 6** — Return `s.substring(start, start + maxLen)`.

---

## Start Index Formula

When you find a palindrome of length `best` centered at `i`:

```java
start = i - (best - 1) / 2;
```

Example:
```
s = "babad", i=2, best=3 (odd)
start = 2 - (3-1)/2 = 2 - 1 = 1
s.substring(1, 1+3) = "aba"  ✓
```

---

## Code

```java
class Solution {

    public String longestPalindrome(String s) {
        int start = 0, maxLen = 1;

        for (int i = 0; i < s.length(); i++) {

            // Case 1: Odd length → center at i
            int len1 = expand(s, i, i);

            // Case 2: Even length → center between i and i+1
            int len2 = expand(s, i, i + 1);

            int best = Math.max(len1, len2);

            if (best > maxLen) {
                maxLen = best;
                start = i - (best - 1) / 2;
            }
        }

        return s.substring(start, start + maxLen);
    }

    private int expand(String s, int L, int R) {
        while (L >= 0 && R < s.length() && s.charAt(L) == s.charAt(R)) {
            L--;
            R++;
        }
        // L and R are one step beyond the valid palindrome
        return R - L - 1;
    }
}
```

---

## Dry Run

**Input:** `s = "cbbd"`

```
Initialize: start=0, maxLen=1

i=0, char='c'
  expand(0,0): L=0 R=0 → L=-1 R=1  (b, no match)  → len = 1-(-1)-1 = 1
  expand(0,1): L=0 R=1 → c≠b → stop immediately    → len = 1-0-1 = 0
  best = 1   no update

i=1, char='b'
  expand(1,1): L=1 R=1 → L=0 R=2 → c≠b → stop      → len = 2-0-1 = 1
  expand(1,2): L=1 R=2 → b==b ✓ → L=0 R=3 → c≠d → stop  → len = 3-0-1 = 2
  best = 2   → maxLen=2, start = 1-(2-1)/2 = 1

i=2, char='b'
  expand(2,2): L=2 R=2 → L=1 R=3 → b≠d → stop      → len = 1
  expand(2,3): L=2 R=3 → b≠d → stop                 → len = 0
  best = 1   no update

i=3, char='d'
  expand(3,3): len = 1
  expand(3,4): R=4 out of bounds → len = 0
  best = 1   no update

Final: s.substring(1, 1+2) = "bb"
```

**Output:** `"bb"` ✓

---

## Time Complexity

```
Outer loop:        O(N)
Each expand call:  O(N) worst case

Total:             O(N²)
```

Space: **O(1)** — no extra arrays, only two integers tracked.

---

## Common Mistakes

### Mistake 1 — Forgetting even-length case

```java
// WRONG — only handles odd palindromes
int len = expand(s, i, i);

// RIGHT — always call both
int len1 = expand(s, i, i);
int len2 = expand(s, i, i + 1);
```

"aabbaa" has center between index 2 and 3. Missing even case misses it entirely.

### Mistake 2 — Wrong length formula

```java
// WRONG
return R - L + 1;   // off by 2 because L and R overshot

// RIGHT
return R - L - 1;   // compensates for the one extra step on each side
```

### Mistake 3 — Wrong start index calculation

```java
// WRONG
start = i;

// RIGHT
start = i - (best - 1) / 2;
// This works for both odd and even lengths
```

### Mistake 4 — Checking only from i=1

```java
// WRONG — misses palindromes centered at index 0
for (int i = 1; i < s.length(); i++)

// RIGHT
for (int i = 0; i < s.length(); i++)
```

---

## Interview Explanation

> "I use the expand-from-center technique. For each index, I treat it as the center of a palindrome and expand outward while characters match. I handle both odd-length and even-length palindromes separately. Each expansion is O(N) in the worst case, making the total time O(N²) with O(1) space."

---

## Comparison With Other Approaches

| Approach | Time | Space | Notes |
|----------|------|-------|-------|
| Brute force (check all substrings) | O(N³) | O(1) | Too slow |
| Expand from center | O(N²) | O(1) | ✅ Standard interview answer |
| Dynamic programming | O(N²) | O(N²) | Same time, worse space |
| Manacher's algorithm | O(N) | O(N) | Optimal but never asked in interviews |

Expand from center is the expected answer in interviews. It is simple to explain, simple to code, and has optimal space.

---

## Key Insight

```
Opposite direction: you know the ends, verify inward.
Expand from center: you know the center, discover the ends.
```

Same two-pointer movement, opposite direction of discovery.

---

## Pattern Tracker

| Field | Value |
|-------|-------|
| Problem | LC5 Longest Palindromic Substring |
| Difficulty | Medium |
| Technique | Expand from center |
| Key formula | `length = R - L - 1` after loop exits |
| Two cases | `expand(i,i)` odd, `expand(i,i+1)` even |
| Start index | `i - (best-1)/2` |
| Time | O(N²) |
| Space | O(1) |

---

## Recognition Signal

See this pattern when:
```
✓ "Longest palindromic ..."
✓ "Palindrome inside a string"
✓ "Find a palindrome" (not verify one)
```

Contrast with LC125/LC680:
```
"Is this string a palindrome?" → Opposite direction pointers
"Find the longest palindrome"  → Expand from center
```
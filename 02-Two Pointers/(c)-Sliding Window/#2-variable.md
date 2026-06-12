# Variable Sliding Window

> Expand when valid. Shrink when invalid.

---

## Core Idea

Window size changes dynamically.

Visual:

```text
Expand →

[L.......R]

Condition breaks

Shrink ←
```

---

## Recognition Signals

Look for:

* Longest
* Shortest
* At Most K
* At Least K
* Distinct Characters
* Minimum Window

---

## Generic Template

```java
int left = 0;

for(int right = 0; right < n; right++) {

    // expand

    while(conditionBroken) {

        // shrink
        left++;
    }

    // update answer
}
```

---

# Example Problems

## LC209 - Minimum Size Subarray Sum

### Goal

Smallest subarray whose sum ≥ target.

Example:

```text
target = 7

[2,3,1,2,4,3]

Answer = 2
```

### Code

```java
class Solution {

    public int minSubArrayLen(
            int target,
            int[] nums) {

        int left = 0;
        int sum = 0;
        int ans = Integer.MAX_VALUE;

        for(int right = 0;
            right < nums.length;
            right++) {

            sum += nums[right];

            while(sum >= target) {

                ans = Math.min(
                        ans,
                        right - left + 1);

                sum -= nums[left];
                left++;
            }
        }

        return ans == Integer.MAX_VALUE
                ? 0
                : ans;
    }
}
```

Time: O(N)

Space: O(1)

---

## LC3 - Longest Substring Without Repeating Characters

### Goal

Maintain unique characters.

### Code

```java
class Solution {

    public int lengthOfLongestSubstring(
            String s) {

        Set<Character> set =
                new HashSet<>();

        int left = 0;
        int ans = 0;

        for(int right = 0;
            right < s.length();
            right++) {

            while(set.contains(
                    s.charAt(right))) {

                set.remove(
                        s.charAt(left));

                left++;
            }

            set.add(s.charAt(right));

            ans = Math.max(
                    ans,
                    right-left+1);
        }

        return ans;
    }
}
```

Time: O(N)

Space: O(K)

---

## LC424 - Longest Repeating Character Replacement

### Goal

At most K replacements allowed.

### Key Idea

```text
Window Size
-
Most Frequent Character

<= K
```

### Code

```java
class Solution {

    public int characterReplacement(
            String s,
            int k) {

        int[] freq = new int[26];

        int left = 0;
        int maxFreq = 0;
        int ans = 0;

        for(int right = 0;
            right < s.length();
            right++) {

            maxFreq = Math.max(
                    maxFreq,
                    ++freq[s.charAt(right)-'A']);

            while(
                (right-left+1)-maxFreq > k) {

                freq[s.charAt(left)-'A']--;
                left++;
            }

            ans = Math.max(
                    ans,
                    right-left+1);
        }

        return ans;
    }
}
```

Time: O(N)

Space: O(1)

---

## LC1004 - Max Consecutive Ones III

### Goal

Flip at most K zeros.

### Idea

Maintain valid window.

Time: O(N)

Space: O(1)

---

## LC76 - Minimum Window Substring

### Goal

Classic shrinking window problem.

### Learning Outcome

Master-level sliding window.

Time: O(N)

Space: O(K)

---

# Pattern Tracker

```text
Pattern:
Variable Window

Recognition:
Longest
Shortest
At Most K
At Least K

Core Idea:
Expand
Shrink
Maintain

Complexity:
O(N)
```

---

# One-Line Revision

```text
Variable Window =
Grow when possible,
shrink when necessary.
```

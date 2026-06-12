# Fixed Sliding Window

> Window size is constant.

---

## Core Idea

A window of size `K` moves across the array/string.

Instead of recalculating every window:

```text
Remove left element
+
Add right element
```

---

## Recognition Signals

Look for:

* Size K
* Length K
* Exactly K elements
* Fixed-length substring
* Fixed-length subarray

---

## Mental Model

```text
[1 2 3] 4 5

↓

1 [2 3 4] 5

↓

1 2 [3 4 5]
```

Window size never changes.

---

## Generic Template

```java
int windowSum = 0;

// First window
for(int i = 0; i < k; i++) {
    windowSum += nums[i];
}

for(int right = k; right < nums.length; right++) {

    windowSum += nums[right];
    windowSum -= nums[right - k];

    // process current window
}
```

---

# Example Problems

## LC643 - Maximum Average Subarray I

### Goal

Find maximum average of any subarray of size K.

Example:

```text
nums = [1,12,-5,-6,50,3]
k = 4

Answer = 12.75
```

### Idea

Maintain sum of current window.

Move window by:

```text
Add new element

Remove old element
```

### Code

```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {

        int sum = 0;

        for(int i = 0; i < k; i++)
            sum += nums[i];

        int maxSum = sum;

        for(int i = k; i < nums.length; i++) {

            sum += nums[i];
            sum -= nums[i-k];

            maxSum = Math.max(maxSum, sum);
        }

        return (double) maxSum / k;
    }
}
```

Time: O(N)

Space: O(1)

---

## LC1456 - Maximum Number of Vowels in a Substring of Given Length

### Goal

Find maximum vowels in any substring of length K.

Example:

```text
s = "abciiidef"
k = 3

Answer = 3
```

### Idea

Maintain vowel count inside window.

### Code

```java
class Solution {

    public int maxVowels(String s, int k) {

        int count = 0;

        for(int i = 0; i < k; i++) {
            if(isVowel(s.charAt(i)))
                count++;
        }

        int max = count;

        for(int i = k; i < s.length(); i++) {

            if(isVowel(s.charAt(i)))
                count++;

            if(isVowel(s.charAt(i-k)))
                count--;

            max = Math.max(max, count);
        }

        return max;
    }

    private boolean isVowel(char c) {
        return "aeiou".indexOf(c) != -1;
    }
}
```

Time: O(N)

Space: O(1)

---

## LC1343 - Number of Subarrays of Size K and Average ≥ Threshold

### Goal

Count valid windows.

### Idea

Sliding sum + average check.

### Code

```java
class Solution {
    public int numOfSubarrays(
            int[] arr,
            int k,
            int threshold) {

        int target = k * threshold;

        int sum = 0;

        for(int i = 0; i < k; i++)
            sum += arr[i];

        int count = (sum >= target) ? 1 : 0;

        for(int i = k; i < arr.length; i++) {

            sum += arr[i];
            sum -= arr[i-k];

            if(sum >= target)
                count++;
        }

        return count;
    }
}
```

Time: O(N)

Space: O(1)

---

# Pattern Tracker

```text
Pattern:
Fixed Window

Recognition:
Size K
Length K
Exactly K

Core Idea:
Add Right
Remove Left

Complexity:
O(N)
```

---

# One-Line Revision

```text
Fixed Window =
Same size,
different position.
```

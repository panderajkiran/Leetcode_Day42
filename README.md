# Leetcode_Day42
# Day 42: Maximum Average Subarray I

## LeetCode Problem 643

**Difficulty:** Easy
**Topic:** Array, Sliding Window

### Problem Statement

Given an integer array `nums` and an integer `k`, find a contiguous subarray of length exactly `k` that has the maximum average value.

Return the maximum average.

### Example

**Input:**

```text
nums = [1, 12, -5, -6, 50, 3], k = 4
```

**Output:**

```text
12.75
```

**Explanation:**

The subarray `[12, -5, -6, 50]` has the maximum sum:

```text
12 + (-5) + (-6) + 50 = 51
```

Average:

```text
51 / 4 = 12.75
```

### Approach: Sliding Window

Instead of calculating the sum of every subarray separately, we use the **sliding window** technique.

1. Calculate the sum of the first `k` elements.
2. Store this sum as the maximum sum.
3. Move the window one position at a time.
4. Add the new element entering the window.
5. Subtract the element leaving the window.
6. Update the maximum sum.
7. Return the maximum sum divided by `k`.

This avoids repeatedly calculating the sum of each subarray.

### Java Solution

```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        int sum = 0;

        for (int i = 0; i < k; i++) {
            sum += nums[i];
        }

        int maxSum = sum;

        for (int i = k; i < nums.length; i++) {
            sum += nums[i] - nums[i - k];
            maxSum = Math.max(maxSum, sum);
        }

        return (double) maxSum / k;
    }
}
```

### Complexity Analysis

* **Time Complexity:** `O(n)` — Each element is processed at most once.
* **Space Complexity:** `O(1)` — Only a few variables are used.

### What I Learned

* How to use the sliding window technique.
* How to calculate the sum of a fixed-size subarray efficiently.
* How to avoid unnecessary repeated calculations.
* Why casting to `double` is important when returning an average.

### Key Takeaway

A problem that looks like it requires checking every subarray can often be solved more efficiently by reusing the work already done. Sometimes, the best optimization is simply to stop calculating the same thing again and again.

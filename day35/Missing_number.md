# Missing Number (LeetCode 268)

## Problem Statement
Given an array `nums` containing **n distinct numbers** in the range `[0, n]`, return the **only number in the range that is missing** from the array.

---

## Examples

### Example 1
**Input:**
```
nums = [3, 0, 1]
```
**Output:**
```
2
```
**Explanation:**
- `n = 3`, so the numbers should be `[0, 1, 2, 3]`.
- The number `2` is missing.

---

### Example 2
**Input:**
```
nums = [0, 1]
```
**Output:**
```
2
```
**Explanation:**
- `n = 2`, so the numbers should be `[0, 1, 2]`.
- The number `2` is missing.

---

### Example 3
**Input:**
```
nums = [9, 6, 4, 2, 3, 5, 7, 0, 1]
```
**Output:**
```
8
```
**Explanation:**
- `n = 9`, so the numbers should be `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`.
- The number `8` is missing.

---

## Constraints
- `n == nums.length`
- `1 <= n <= 10^4`
- `0 <= nums[i] <= n`
- All numbers of `nums` are **unique**.

---

## Approach

We know that the sum of the first `n` natural numbers (including `0`) is:

\[
\text{Expected Sum} = \frac{n \cdot (n + 1)}{2}
\]

Steps:
1. Calculate the expected sum of numbers from `0` to `n`.
2. Find the actual sum of elements in the given array.
3. The missing number is:
\[
\text{Missing Number} = \text{Expected Sum} - \text{Actual Sum}
\]

---

## C++ Solution

```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int sz = nums.size();
        int sum = 0;
        for (int i : nums) sum += i;
        return ((sz * (sz + 1)) / 2) - sum;
    }
};
```

---

## Complexity Analysis
- **Time Complexity:** `O(n)` — we iterate once over the array.
- **Space Complexity:** `O(1)` — only constant extra memory is used.

---

## Alternative Approaches
1. **XOR Approach**  
   - XOR all numbers from `0` to `n` and XOR with all numbers in the array.  
   - The duplicate numbers cancel out, leaving the missing number.

2. **Sorting Approach**  
   - Sort the array.  
   - Check if the element at each index matches the index value.  
   - The first mismatch is the missing number.  

---

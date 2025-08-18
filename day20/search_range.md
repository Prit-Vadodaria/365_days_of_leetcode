# 🔍 Find First and Last Position of Element in Sorted Array

## Problem Statement

Given an array of integers `nums` sorted in **non-decreasing order**,
find the **starting** and **ending position** of a given target value.

If target is not found in the array, return `[-1, -1]`.

You must write an algorithm with **O(log n)** runtime complexity.

------------------------------------------------------------------------

## Examples

**Example 1:**

    Input: nums = [5,7,7,8,8,10], target = 8
    Output: [3,4]

**Example 2:**

    Input: nums = [5,7,7,8,8,10], target = 6
    Output: [-1,-1]

**Example 3:**

    Input: nums = [], target = 0
    Output: [-1,-1]

------------------------------------------------------------------------

## Constraints

-   `0 <= nums.length <= 10^5`\
-   `-10^9 <= nums[i] <= 10^9`\
-   `nums` is sorted in **non-decreasing order**\
-   `-10^9 <= target <= 10^9`

------------------------------------------------------------------------

## Solution Approach

We perform **two binary searches**: 1. One to find the **first
occurrence** of the target. 2. One to find the **last occurrence** of
the target.

Both run in **O(log n)** time.

------------------------------------------------------------------------

## C++ Solution

``` cpp
class Solution {
public:
    int findFirst(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1, ans = -1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] >= target) {
                if (nums[mid] == target) ans = mid;
                right = mid - 1; 
            } else {
                left = mid + 1;
            }
        }
        return ans;
    }
    
    int findLast(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1, ans = -1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] <= target) {
                if (nums[mid] == target) ans = mid;
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return ans;
    }

    vector<int> searchRange(vector<int>& nums, int target) {
        int first = findFirst(nums, target);
        int last = findLast(nums, target);
        return {first, last};
    }
};
```

------------------------------------------------------------------------

## ✅ Key Points

-   Uses **binary search** → O(log n).\
-   Works on empty arrays.\
-   Returns `[-1, -1]` when target not found.

------------------------------------------------------------------------

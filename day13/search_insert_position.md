# Search Insert Position

Given a sorted array of **distinct integers** and a target value, return the index if the target is found.  
If not, return the index where it would be if it were inserted in order.

You must write an algorithm with **O(log n)** runtime complexity.

---

## ✨ Examples

### Example 1:
**Input:**  
nums = [1, 3, 5, 6], target = 5  
**Output:**  
2

### Example 2:
**Input:**  
nums = [1, 3, 5, 6], target = 2  
**Output:**  
1

---

## 💡 Explanation

We can solve this problem efficiently using **binary search** because the input array is already sorted.  

**Key Idea:**
- Keep two pointers `left` and `right`.
- Calculate `mid` each time and compare `nums[mid]` with `target`.
- If `target` is found, return `mid`.
- If `target` is greater, search the right half.
- If `target` is smaller, search the left half.
- When the loop ends, `left` will be the correct insertion index.

---

## ✅ Constraints
- 1 <= nums.length <= 10⁴
- -10⁴ <= nums[i], target <= 10⁴
- All integers in `nums` are **distinct**.

---

## 💻 C++ Solution

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            
            if (nums[mid] == target) {
                return mid; // Found exact match
            } 
            else if (nums[mid] < target) {
                left = mid + 1; // Search in right half
            } 
            else {
                right = mid - 1; // Search in left half
            }
        }
        
        // If not found, left is the insertion index
        return left;
    }
};


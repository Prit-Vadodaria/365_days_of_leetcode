# 📊 Median of Two Sorted Arrays – C++ Solution

## 📝 Problem Statement

You are given **two sorted arrays** `nums1` and `nums2` of sizes `m` and `n` respectively. Return the **median** of the two sorted arrays.

⚠️ The **overall run time complexity** should be `O(log (m+n))`.

---

## 📥 Input / 📤 Output

### Input
- Two sorted integer arrays `nums1` and `nums2`.

### Output
- A **floating-point number** representing the median of the combined sorted array.

---

## 💡 Examples

### Example 1:
Input: nums1 = [1, 3], nums2 = [2]
Output: 2.00000
Explanation: Merged = [1, 2, 3]; median = 2

### Example 2:
Input: nums1 = [1, 2], nums2 = [3, 4]
Output: 2.50000
Explanation: Merged = [1, 2, 3, 4]; median = (2 + 3) / 2 = 2.5

---

## 📌 Constraints

- `0 <= nums1.length, nums2.length <= 1000`
- `1 <= nums1.length + nums2.length <= 2000`
- `-10⁶ <= nums1[i], nums2[i] <= 10⁶`
- Both `nums1` and `nums2` are **sorted in non-decreasing order**

---

## 🚀 Approach: Brute-Force Merge & Sort

### 🔧 Idea

1. Combine both input arrays into a single vector.
2. Sort the merged vector.
3. If the combined size is odd, return the middle element.
4. If even, return the average of the two middle elements.

---

## ✅ C++ Implementation

```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        vector<int> merged = nums1;
        for (int i = 0; i < nums2.size(); i++) {
            merged.push_back(nums2[i]); // merge second array
        }
        sort(merged.begin(), merged.end()); // sort merged array
        int sz = merged.size();
        if (sz % 2 == 0) {
            return (merged[sz / 2 - 1] + merged[sz / 2]) / double(2);
        }
        return merged[sz / 2];
    }
};

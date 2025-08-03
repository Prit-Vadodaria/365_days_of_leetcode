# 🧱 Container With Most Water

## 📝 Problem Statement

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the *i<sup>th</sup>* line are `(i, 0)` and `(i, height[i])`.

Find **two lines** that, together with the x-axis, form a **container** that holds the **maximum amount of water**.

**Note:** You may **not slant** the container.

---

## 🔍 Example

### Example 1:

Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49


📘 **Explanation**:  
Lines at index `1` and `8` form the container with height = min(8, 7) = 7 and width = 8 - 1 = 7.  
So the area = 7 × 7 = **49** (maximum possible).

### Example 2:

Input: height = [1,1]
Output: 1

---

## ✅ Constraints

- `n == height.length`
- `2 <= n <= 10⁵`
- `0 <= height[i] <= 10⁴`

---

## 💡 Approach

This problem is optimally solved using the **Two Pointer Technique**.

### 🔧 Steps:
1. Initialize two pointers: `left` at 0 and `right` at `n - 1`.
2. Calculate the **area** between the lines at these pointers:
   - `height = min(height[left], height[right])`
   - `width = right - left`
   - `area = height * width`
3. Update `maxArea` if the current area is larger.
4. Move the pointer pointing to the **shorter line** inward to try finding a potentially larger container.
5. Repeat until `left < right`.

---

## 🧪 C++ Code

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int left = 0, right = height.size() - 1;
        int maxArea = 0;

        while (left < right) {
            int h = min(height[left], height[right]);
            int width = right - left;
            maxArea = max(maxArea, h * width);

            // Move the shorter line inward
            if (height[left] < height[right])
                left++;
            else
                right--;
        }

        return maxArea;
    }
};

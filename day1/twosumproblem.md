# 🧮 Two Sum Problem – C++ Solution

## 📝 Problem Statement

Given an array of integers `nums` and an integer `target`, return **the indices of the two numbers** such that they add up to the target.

**Conditions:**
- Exactly **one solution** exists.
- You **cannot** use the same element twice.
- Return the answer in **any order**.

---

## 📥 Input / 📤 Output

### Input
- An array `nums` of integers (2 ≤ nums.length ≤ 10⁴)
- An integer `target` (−10⁹ ≤ nums[i], target ≤ 10⁹)

### Output
- A vector (array) containing **two indices** `i` and `j` such that `nums[i] + nums[j] == target`.

---

## 💡 Example

### Example 1:
nput: nums = [2, 7, 11, 15], target = 9
Output: [0, 1]
Explanation: nums[0] + nums[1] = 2 + 7 = 9


### Example 2:
Input: nums = [3, 3], target = 6
Output: [0, 1]


### Example 3:
Input: nums = [3, 2, 4], target = 6
Output: [1, 2]


---

## 🚀 Approach

### 🔁 Brute Force (Nested Loops)
This solution uses a brute-force approach:

1. Traverse each element in the array using two nested loops.
2. For each pair `(i, j)` where `j > i`, check if `nums[i] + nums[j] == target`.
3. If found, return the indices `[i, j]`.

### ✅ Why This Works
- The problem guarantees **exactly one solution**, so we return immediately once we find a valid pair.
- Using a **return** as soon as the result is found improves efficiency slightly in practice.

---

## 🧠 Code Explanation

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> result;
        for(int i = 0; i < nums.size(); i++) {
            for(int j = i + 1; j < nums.size(); j++) {
                if(nums[i] + nums[j] == target) {
                    result.push_back(i);
                    result.push_back(j);
                    return result; // Return immediately after finding the pair
                }
            }
        }
        return result; // Just a fallback; won't be hit due to problem constraints
    }
};

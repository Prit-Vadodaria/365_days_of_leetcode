
# Remove Element

## Problem Statement
Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` **in-place**.  
The order of the elements may be changed. Then return the number of elements in `nums` which are not equal to `val`.

---

## Details
Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

1. Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`.
2. The remaining elements of `nums` are not important as well as the size of `nums`.
3. Return `k`.

---

## Custom Judge
The judge will test your solution with the following code:
```cpp
int[] nums = [...]; // Input array
int val = ...; // Value to remove
int[] expectedNums = [...]; // Expected result with correct length, no elements equal to val.

int k = removeElement(nums, val); // Calls your implementation

assert k == expectedNums.length;
sort(nums, 0, k); // Sort the first k elements of nums
for (int i = 0; i < actualLength; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, your solution will be accepted.

---

## Examples

**Example 1:**
```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Function returns k = 2, first two elements are 2.
```

**Example 2:**
```
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
Explanation: Function returns k = 5, first five elements are 0, 1, 4, 0, 3 in any order.
```

---

## Constraints
- 0 <= nums.length <= 100
- 0 <= nums[i] <= 50
- 0 <= val <= 100

---

## C++ Solution
```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        for(int i = 0; i < nums.size(); i++) {
            if(nums[i] == val) {
                for(int j = i; j < nums.size(); j++) {
                    if(j == nums.size() - 1) {
                        break;
                    }
                    nums[j] = nums[j + 1];
                }
                nums.resize(nums.size() - 1);
                i--;
            }
        }
        return nums.size();
    }
};
```

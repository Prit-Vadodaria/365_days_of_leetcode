# Remove Duplicates from Sorted Array 🔁

An optimized C++ solution to remove duplicates from a **sorted array in-place**, ensuring that each unique element appears only once while maintaining the original relative order.

---

## 🛠️ Tech Stack

- **C++** – Efficient algorithmic implementation.
- **STL Vector** – Used for dynamic array manipulation.
- **Time Complexity** – O(n), where n is the size of the input array.

---

## 📸 Features

- ✅ Removes duplicates from a non-decreasing sorted array.
- 📦 Modifies the input array in-place with O(1) extra memory.
- 📈 Returns the count `k` of unique elements.
- 🔁 Preserves relative order of unique values.

---

## ▶️ How to Use

1. Define a sorted array `nums`.
2. Call `removeDuplicates(nums)` using an instance of `Solution`.
3. The function returns `k`, the count of unique elements.
4. The first `k` elements of `nums` will be the unique elements in order.

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0;
        int k = 1;
        for (int i = 1; i < nums.size(); ++i) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
};
```

---

👨‍💻 Author  
Prit Vadodaria  
Student at Birla Vishvakarma Mahavidyalaya  
GitHub | LinkedIn
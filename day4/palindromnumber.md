# 🔁 Palindrome Number – C++ Solution

## 📝 Problem Statement

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

An integer is a palindrome when it **reads the same forward and backward**.

---

## 📥 Input / 📤 Output

### Input
- An integer `x` such that `−2³¹ <= x <= 2³¹ − 1`

### Output
- A boolean value: `true` if `x` is a palindrome, otherwise `false`

---

## 💡 Examples

### Example 1:
Input: x = 121
Output: true
Explanation: Reads the same forward and backward.

### Example 2:
Input: x = -121
Output: false
Explanation: Reversed: "121-" is not equal to "-121"

### Example 3:
Input: x = 10
Output: false
Explanation: Reversed: "01" ≠ "10"

---

## ✅ C++ Implementation (String-Based Approach)

```cpp
#include <string>
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0) return false; // Negative numbers are not palindromes

        string rev_num = to_string(x);   // Convert to string
        string num = rev_num;
        reverse(rev_num.begin(), rev_num.end()); // Reverse string

        return num == rev_num; // Compare original and reversed
    }
};
```

Another Aproach:without converting number to string

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) return false;

        int reversed = 0;
        while (x > reversed) {
            reversed = reversed * 10 + x % 10;
            x /= 10;
        }

        return x == reversed || x == reversed / 10;
    }
};
```

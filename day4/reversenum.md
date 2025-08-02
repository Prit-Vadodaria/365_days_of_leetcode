# 🔁 Reverse Integer – C++ Solution

## 📝 Problem Statement

Given a signed 32-bit integer `x`, return `x` **with its digits reversed**.  
If reversing `x` causes the value to go **outside the signed 32-bit integer range** `[-2³¹, 2³¹ - 1]`, return `0`.

📌 **Note:** You cannot use 64-bit integers in your solution.

---

## 📥 Input / 📤 Output

### Input
- A single integer `x` such that `-2³¹ ≤ x ≤ 2³¹ - 1`

### Output
- An integer representing the reversed number, or `0` if it overflows

---

## 💡 Examples

### Example 1:
Input: x = 123
Output: 321


### Example 2:
Input: x = -123
Output: -321


### Example 3:
Input: x = 120
Output: 21

---

## ✅ C++ Implementation

```cpp
class Solution {
public:
    int reverse(int x) {
        int reversed = 0;

        while (x != 0) {
            int digit = x % 10;
            x /= 10;

            // Check for overflow before multiplying or adding
            if (reversed > INT_MAX / 10 || (reversed == INT_MAX / 10 && digit > 7)) return 0;
            if (reversed < INT_MIN / 10 || (reversed == INT_MIN / 10 && digit < -8)) return 0;

            reversed = reversed * 10 + digit;
        }

        return reversed;
    }
};
```
🔧 Approach & Explanation
Extract the last digit of x using x % 10.

Append it to the reversed number using multiplication and addition.

Carefully check for overflow/underflow before performing operations:

INT_MAX = 2147483647 → last digit must not exceed 7

INT_MIN = -2147483648 → last digit must not be less than -8

Return 0 if the reverse would exceed 32-bit limits.

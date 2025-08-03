# 🔢 String to Integer (atoi) – C++ Solution

## 📝 Problem Statement

Implement the `myAtoi(string s)` function, which converts a string to a **32-bit signed integer** (similar to the C/C++ `atoi` function).

### The conversion rules are:
1. **Ignore leading whitespace** characters.
2. **Detect the sign** of the number (`+` or `-`). If none, assume positive.
3. **Convert digit characters** into an integer until a non-digit character or the end of the string is reached.
4. **Clamp** the result to the 32-bit signed integer range:  
   - Minimum: `-2³¹` → `-2147483648`  
   - Maximum: `2³¹ - 1` → `2147483647`
5. **Return** the computed integer.

---

## 📥 Input / 📤 Output

### Input:
- A string `s` consisting of whitespace, digits, letters, `'+'`, `'-'`, and `'.'`

### Output:
- A 32-bit signed integer based on parsed conversion

---

## 💡 Examples

### Example 1:
nput: s = "42"
Output: 42

### Example 2:
Input: s = " -042"
Output: -42


### Example 3:
Input: s = "1337c0d3"
Output: 1337

### Example 4:
Input: s = "0-1"
Output: 0

### Example 5:
Input: s = "words and 987"
Output: 0

---

## ✅ C++ Implementation

```cpp
class Solution {
public:
    int myAtoi(string s) {
        int index = 0;
        int n = s.length();
        long num = 0;
        int sign = 1;

        // Skip leading whitespaces
        while (index < n && s[index] == ' ')
            index++;

        // Check for sign
        if (index < n && (s[index] == '-' || s[index] == '+')) {
            sign = (s[index] == '-') ? -1 : 1;
            index++;
        }

        // Convert digits
        while (index < n && isdigit(s[index])) {
            int digit = s[index] - '0';
            num = num * 10 + digit;

            // Overflow check
            if (sign == 1 && num > INT_MAX) return INT_MAX;
            if (sign == -1 && -num < INT_MIN) return INT_MIN;

            index++;
        }

        return static_cast<int>(num * sign);
    }
};
```
🔍 Approach & Explanation
Whitespace Trimming: Skip all leading whitespace characters.

Sign Detection: Handle '+' or '-' to determine the sign of the number.

Digit Parsing: Convert characters to integers and build the number.

Overflow Control:

Use a long to temporarily store the number during conversion.

Check bounds on every digit addition:

Return INT_MAX if value exceeds 32-bit signed max.

Return INT_MIN if value falls below signed min.

Return the final value after applying the correct sign.

---

📌 Constraints
0 <= s.length <= 200

s consists of:

Upper and lowercase English letters

Digits 0-9

Whitespace ' '

Characters '+', '-', and '.'

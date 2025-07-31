# 🔠 Longest Substring Without Repeating Characters – C++ Solution

## 📝 Problem Statement

Given a string `s`, find the **length of the longest substring** without repeating characters.

A **substring** is a contiguous sequence of characters within a string (not to be confused with a subsequence).

---

## 📥 Input / 📤 Output

### Input
- A single string `s`, consisting of English letters, digits, symbols, and spaces.
- Constraints: `0 <= s.length <= 5 * 10⁴`

### Output
- An integer representing the length of the longest substring with no repeating characters.

---

## 💡 Example

### Example 1:
nput: s = "abcabcbb"
Output: 3
Explanation: The longest substring is "abc"

### Example 2:
Input: s = "bbbbb"
Output: 1
Explanation: The longest substring is "b"

### Example 3:
Input: s = "pwwkew"
Output: 3
Explanation: The longest substring is "wke"


---

## 🚀 Approach

### 🔁 Brute-Force with Nested Loops
- Start at each character in the string.
- Try building the longest substring by **appending one character at a time** until a duplicate is found.
- Use `std::string::find()` to detect if a character is already present in the growing substring.
- Keep track of the **maximum length** found across all such attempts.

---

## 📌 C++ Implementation

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int sz = s.length();
        int max_len = 0;

        for (int i = 0; i < sz; i++) {
            string dummy;
            dummy += s[i];
            for (int j = i + 1; j < sz; j++) {
                if (dummy.find(s[j]) != std::string::npos) {
                    break;
                }
                dummy += s[j];
            }
            int len = dummy.length();
            if (len > max_len) {
                max_len = len;
            }
        }

        return max_len;
    }
};

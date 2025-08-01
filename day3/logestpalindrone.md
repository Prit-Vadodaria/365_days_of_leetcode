# 🔁 Longest Palindromic Substring – C++ Solution

## 📝 Problem Statement

Given a string `s`, return the **longest palindromic substring** in `s`.

A **palindrome** is a string that reads the same forward and backward. You may assume there will always be one unique longest palindromic substring.

---

## 📥 Input / 📤 Output

### Input
- A single string `s` of length between `1` and `1000`, consisting only of English letters and digits.

### Output
- A string representing the longest palindromic substring in `s`.

---

## 💡 Examples

### Example 1:
Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.

### Example 2:
Input: s = "cbbd"
Output: "bb"

---

## 🚀 Approach: Expand Around Center

### 🔧 Idea

- A palindrome mirrors around its center.
- There are `2n - 1` centers in a string of length `n` (every character and every gap between characters).
- Expand around each center to find the longest palindromic substring.

### 🪜 Steps

1. Initialize `start = 0` and `maxlen = 1` to track the longest palindrome.
2. Loop through each character:
   - Expand for **odd-length** palindromes centered at `i`.
   - Expand for **even-length** palindromes centered between `i` and `i+1`.
3. Use a lambda function `expandaroundcenter(left, right)` to expand as long as the substring remains a palindrome.
4. Update `start` and `maxlen` if a longer palindrome is found.
5. Return the substring using `s.substr(start, maxlen)`.

---

## ✅ C++ Implementation

```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        int start = 0, maxlen = 1;
        int n = s.length();

        auto expandaroundcenter = [&](int left, int right) {
            while (left >= 0 && right < n && s[left] == s[right]) {
                if (right - left + 1 > maxlen) {
                    maxlen = right - left + 1;
                    start = left;
                }
                left--;
                right++;
            }
        };

        for (int i = 0; i < n; i++) {
            expandaroundcenter(i, i);     // Odd-length palindrome
            expandaroundcenter(i, i + 1); // Even-length palindrome
        }

        return s.substr(start, maxlen);
    }
};

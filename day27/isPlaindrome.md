# Valid Palindrome

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward.  
Alphanumeric characters include letters and numbers.

---

## Problem Statement

Given a string `s`, return **true** if it is a palindrome, or **false** otherwise.

---

### Example 1
**Input:**  
`s = "A man, a plan, a canal: Panama"`  

**Output:**  
`true`  

**Explanation:**  
After removing non-alphanumeric characters and converting to lowercase,  
`"amanaplanacanalpanama"` is a palindrome.

---

### Example 2
**Input:**  
`s = "race a car"`  

**Output:**  
`false`  

**Explanation:**  
After formatting, `"raceacar"` is not a palindrome.

---

### Example 3
**Input:**  
`s = " "`  

**Output:**  
`true`  

**Explanation:**  
After formatting, `s = ""`.  
Since an empty string reads the same forward and backward, it is a palindrome.

---

## Constraints
- `1 <= s.length <= 2 * 10^5`  
- `s` consists only of printable ASCII characters.  

---

## Solution (C++)
```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int sz = s.length();
        if (sz == 0) return true;
        
        string fs = ""; // formatted string
        for (int i = 0; i < sz; i++) {
            if (isalnum(s[i])) {
                fs += tolower(s[i]);
            }
        }
        
        string og = fs;
        reverse(fs.begin(), fs.end());
        return og == fs;
    }
};

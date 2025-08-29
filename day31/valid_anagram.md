# Valid Anagram

## Problem
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

An **Anagram** is a word or phrase formed by rearranging the letters of another, using all the original letters exactly once.

---

## Examples

**Example 1:**
```
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**
```
Input: s = "rat", t = "car"
Output: false
```

---

## Constraints
- `1 <= s.length, t.length <= 5 * 10^4`
- `s` and `t` consist of lowercase English letters.

---

## C++ Solution
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.length()!=t.length()) return false;
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        for(int i=0; i<s.length(); i++) {
            if(s[i] != t[i]) {
                return false;
            }
        }
        return true;
    }
};
```

---

✅ This solution sorts both strings and compares them.  
- **Time Complexity:** `O(n log n)` (due to sorting)  
- **Space Complexity:** `O(1)` (ignoring sorting overhead)  

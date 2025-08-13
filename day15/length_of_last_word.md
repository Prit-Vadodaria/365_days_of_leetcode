# Length of Last Word

## Problem Statement

Given a string `s` consisting of words and spaces, return the length of the last word in the string.

A word is a maximal substring consisting of non-space characters only.

---

## Examples

**Example 1:**  
Input: `s = "Hello World"`  
Output: `5`  
Explanation: The last word is `"World"` with length 5.

**Example 2:**  
Input: `s = "   fly me   to   the moon  "`  
Output: `4`  
Explanation: The last word is `"moon"` with length 4.

**Example 3:**  
Input: `s = "luffy is still joyboy"`  
Output: `6`  
Explanation: The last word is `"joyboy"` with length 6.

---

## Constraints

- `1 <= s.length <= 10^4`
- `s` consists of only English letters and spaces `' '`.
- There will be at least one word in `s`.

---

## Approach

We can solve this by scanning the string from the end to find the first word's length.

---

## Code Implementation

### Code Version 1

```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int sz = s.length() - 1;
        int newsz = 0;
        if (s[sz] == ' ') {
            for (int i = sz; i >= 0; i--) {
                if (s[i] != ' ') {
                    break;
                }
                sz--;
            }
        }
        for (int i = sz; i >= 0; i--) {
            if (s[i] == ' ') {
                break;
            }
            newsz++;
        }
        return newsz;
    }
};
```

---

### Code Version 2

```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int sz = s.length() - 1;
        int newsz = 0;
        for (int i = sz; i >= 0; i--) {
            if (s[i] != ' ') {
                newsz++;
            } else if (newsz > 0) {
                break;
            }
        }
        return newsz;
    }
};
```

---

## Complexity Analysis

- **Time Complexity:** O(n), where n is the length of the string.
- **Space Complexity:** O(1), since we only use a few variables.

# Longest Common Prefix - README

## 🗓️ Problem Statement

Write a function to find the **longest common prefix** string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

---

## 🔍 Examples

### Example 1:

```text
Input: strs = ["flower", "flow", "flight"]
Output: "fl"
```

### Example 2:

```text
Input: strs = ["dog", "racecar", "car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

---

## ⚠️ Constraints

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lowercase English letters if it is non-empty.

---

## 💡 Approach

We compare characters in the same position across all strings.

### Steps:

1. Use the first string as a reference.
2. For each character in the reference:
   - Check if that character is present in the same position of every other string.
   - If a mismatch is found or any string ends, return the prefix up to that point.
3. If no mismatch occurs, return the full reference string.

---

## ⏱️ Complexity

- **Time Complexity:** `O(n * m)`\
  where `n` is the number of strings and `m` is the length of the shortest string.
- **Space Complexity:** `O(1)` (not counting the output string).

---

## 💪 Code Implementation (C++)

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) return "";

        for (int i = 0; i < strs[0].size(); ++i) {
            char c = strs[0][i];
            for (int j = 1; j < strs.size(); ++j) {
                if (i >= strs[j].size() || strs[j][i] != c) {
                    return strs[0].substr(0, i);
                }
            }
        }
        return strs[0];
    }
};
```

---

## 🔄 Related Topics

- String Matching
- Array Traversal
- Prefix


# 🔀 Zigzag Conversion – C++ Solution

## 📝 Problem Statement

The string `"PAYPALISHIRING"` is written in a **zigzag** pattern on a given number of rows as shown below for `numRows = 3`:

P A H N
A P L S I I G
Y I R

Then read line by line: **"PAHNAPLSIIGYIR"**

Write the code that performs this zigzag conversion given a string `s` and the number of rows `numRows`.

---

## 📥 Input / 📤 Output

### Input
- A string `s` of length between `1` and `1000`
- An integer `numRows` (1 ≤ numRows ≤ 1000)

### Output
- A string that represents the zigzag-converted text, read line by line

---

## 💡 Examples

### Example 1:
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"

### Example 2:
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P I N
A L S I G
Y A H R
P I

### Example 3:
Input: s = "A", numRows = 1
Output: "A"

---

## 🚀 Approach: Simulated Row Writing

### 🔧 Idea

- Think of writing characters in a zigzag form row-by-row.
- Use an array of strings (one for each row).
- Traverse the string while simulating the **vertical down** and **diagonal up** direction using nested loops.
- Append each character to the appropriate row.
- Finally, concatenate all rows.

---

## ✅ C++ Implementation

```cpp
class Solution {
public:
    string convert(string s, int numRows) {
        if(numRows == 1) return s;

        string ct[numRows];
        int n = s.size();
        int cnt = 0;

        while(cnt < n) {
            // Go vertically down
            for(int i = 0; i < numRows && cnt < n; i++) {
                ct[i] += s[cnt++];
            }
            // Go diagonally up
            for(int i = numRows - 2; i > 0 && cnt < n; i--) {
                ct[i] += s[cnt++];
            }
        }

        string ans = "";
        for(int i = 0; i < numRows; i++) {
            ans += ct[i];
        }

        return ans;
    }
};


# Roman to Integer - README

## 📅 Problem Statement

Given a Roman numeral, convert it to an **integer**.

Roman numerals are composed using the following symbols:

| Symbol | Value |
| ------ | ----- |
| M      | 1000  |
| D      | 500   |
| C      | 100   |
| L      | 50    |
| X      | 10    |
| V      | 5     |
| I      | 1     |

### Rules:

- Symbols are placed in order of value, starting with the largest values.
- **Subtractive notation** is used for values like 4, 9, 40, 90, etc.:
  - IV = 4, IX = 9
  - XL = 40, XC = 90
  - CD = 400, CM = 900
- When a smaller value precedes a larger one, it is subtracted from the larger.
- When a larger or equal value precedes a smaller one, it is added.

---

## 🔍 Examples

### Example 1:

```text
Input: s = "III"
Output: 3
Explanation: I + I + I = 3
```

### Example 2:

```text
Input: s = "LVIII"
Output: 58
Explanation: L (50) + V (5) + III (3) = 58
```

### Example 3:

```text
Input: s = "MCMXCIV"
Output: 1994
Explanation:
  - M = 1000
  - CM = 900
  - XC = 90
  - IV = 4
```

---

## ⚠️ Constraints

- `1 <= s.length <= 15`
- `s` contains only the characters: 'I', 'V', 'X', 'L', 'C', 'D', 'M'
- It is guaranteed that `s` is a valid Roman numeral in the range `[1, 3999]`

---

## 💡 Approach

We traverse the Roman numeral string **from right to left**, tracking the total and the previous value:

### Steps:

1. Use a map to convert Roman characters to integers.
2. Start from the last character and move left.
3. For each character:
   - If its value is less than the previous value, subtract it.
   - Otherwise, add it.
4. Return the total.

---

## ⏱️ Complexity

- **Time Complexity:** `O(n)` where `n` is the length of the string.
- **Space Complexity:** `O(1)` - constant space for the map.

---

## 💪 Code Implementation (C++)

```cpp
class Solution {
public:
    unordered_map<char,int> roman = {
        {'I',1}, {'V',5}, {'X',10}, {'L',50},
        {'C',100}, {'D',500}, {'M',1000}
    };

    int romanToInt(string s) {
        int total = 0;
        int prev = 0;
        for (int i = s.length() - 1; i >= 0; i--) {
            int curr = roman[s[i]];
            if (curr < prev) {
                total -= curr;
            } else {
                total += curr;
            }
            prev = curr;
        }
        return total;
    }
};
```

---

## 🔄 Related Topics

- Hash Maps
- Greedy Algorithms
- String Traversal
- Number Systems

---

## 🏆 Conclusion

This solution efficiently handles Roman numeral to integer conversion by processing from right to left and applying the subtraction logic only when necessary. It ensures both correctness and optimal performance.


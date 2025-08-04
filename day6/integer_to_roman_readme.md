# Integer to Roman - README

## 📅 Problem Statement

Given an integer, convert it to a **Roman numeral**.

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
- **Subtractive notation** is used for values like 4, 9, 40, 90, etc.
  - 4 -> IV (one before five)
  - 9 -> IX (one before ten)
  - 40 -> XL, 90 -> XC, 400 -> CD, 900 -> CM
- Symbols like `I`, `X`, `C`, `M` can be repeated at most 3 times.
- Symbols like `V`, `L`, and `D` are **never repeated**.

---

## 🔍 Examples

### Example 1:

```text
Input: num = 3749
Output: "MMMDCCXLIX"
Explanation:
  - 3000 = MMM
  - 700 = DCC
  - 40 = XL
  - 9 = IX
```

### Example 2:

```text
Input: num = 1994
Output: "MCMXCIV"
Explanation:
  - 1000 = M
  - 900 = CM
  - 90 = XC
  - 4 = IV
```

### Example 3:

```text
Input: num = 58
Output: "LVIII"
Explanation:
  - 50 = L
  - 8 = VIII
```

---

## ⚠️ Constraints

- `1 <= num <= 3999`

---

## 💡 Approach

We use a **greedy algorithm** to match the largest Roman numeral value and subtract it from the number until we reach zero.

### Steps:

1. Define a vector of `{value, symbol}` pairs in descending order.
2. Iterate through the vector:
   - While the current number is ≥ the value:
     - Append the symbol to the result.
     - Subtract the value from the number.
3. Return the final Roman numeral string.

---

## ⏱️ Complexity

- **Time Complexity:** `O(1)` - At most constant operations for numbers ≤ 3999.
- **Space Complexity:** `O(1)` - Fixed list of Roman numerals.

---

## 💪 Code Implementation (C++)

```cpp
class Solution {
public:
    vector<pair<int, string>> romint = {
        {1000, "M"}, {900, "CM"}, {500, "D"}, {400, "CD"},
        {100, "C"},  {90, "XC"},  {50, "L"},  {40, "XL"},
        {10, "X"},   {9, "IX"},   {5, "V"},   {4, "IV"},
        {1, "I"}
    };

    string intToRoman(int num) {
        string roman;
        for (auto &[val, sym] : romint) {
            while (num >= val) {
                roman += sym;
                num -= val;
            }
        }
        return roman;
    }
};
```

---

## 🔄 Related Topics

- Greedy Algorithms
- String Manipulation
- Number Systems

---

## 🏆 Conclusion

This method ensures an efficient and correct Roman numeral conversion by leveraging greedy selection of the largest symbols and proper handling of subtractive notation.

Perfect for interviews and competitive programming.


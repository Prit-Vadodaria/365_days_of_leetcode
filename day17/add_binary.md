# Add Binary

## Problem Statement

Given two binary strings `a` and `b`, return their sum as a binary string.

### Example 1:
**Input:**
```
a = "11"
b = "1"
```
**Output:**
```
"100"
```

### Example 2:
**Input:**
```
a = "1010"
b = "1011"
```
**Output:**
```
"10101"
```

**Constraints:**
- 1 <= a.length, b.length <= 10^4
- a and b consist only of '0' or '1' characters.
- Each string does not contain leading zeros except for the zero itself.

---

## Code Implementation

```cpp
class Solution {
public:
    string addBinary(string a, string b) {
        string result = "";
        int i = a.size() - 1;
        int j = b.size() - 1;
        int carry = 0;

        while (i >= 0 || j >= 0 || carry) {
            int sum = carry;
            if (i >= 0) sum += a[i--] - '0'; // convert char to int
            if (j >= 0) sum += b[j--] - '0';

            result.push_back((sum % 2) + '0'); // store current bit
            carry = sum / 2; // update carry
        }

        reverse(result.begin(), result.end()); // reverse because we added from right to left
        return result;
    }
};
```

---

## Approach

1. Start from the end of both strings `a` and `b`.
2. Add corresponding bits and carry from the previous step.
3. Append the current result bit to the `result` string.
4. Update the carry.
5. Continue until all bits and carry are processed.
6. Reverse the result string to get the final binary sum.

# Plus One

## Problem Statement

You are given a large integer represented as an integer array `digits`, where each `digits[i]` is the ith digit of the integer.  
The digits are ordered from most significant to least significant in left-to-right order.  
The large integer does not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.

### Examples

#### Example 1:
**Input:**
```
digits = [1,2,3]
```
**Output:**
```
[1,2,4]
```
**Explanation:** The array represents the integer 123. Incrementing by one gives 123 + 1 = 124.

#### Example 2:
**Input:**
```
digits = [4,3,2,1]
```
**Output:**
```
[4,3,2,2]
```
**Explanation:** The array represents the integer 4321. Incrementing by one gives 4321 + 1 = 4322.

#### Example 3:
**Input:**
```
digits = [9]
```
**Output:**
```
[1,0]
```
**Explanation:** The array represents the integer 9. Incrementing by one gives 9 + 1 = 10.

### Constraints:
- 1 <= digits.length <= 100
- 0 <= digits[i] <= 9
- digits does not contain any leading 0's.

---

## Solution

### C++ Code

```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int sz = digits.size();
        int sum = 1;
        bool flag = false;
        for (int i = sz - 1; i >= 0; i--) {
            sum = digits[i] + sum;
            if (sum < 10) {
                digits[i] = sum;
                break;
            }
            int rem = sum % 10;
            sum /= 10;
            digits[i] = rem;
            flag = true;
        }
        if (sum == 1 && flag) {
            digits.resize(sz + 1);
            for (int i = digits.size() - 1; i > 0; i--) {
                digits[i] = digits[i - 1];
            }
            digits[0] = sum;
        }
        return digits;
    }
};
```


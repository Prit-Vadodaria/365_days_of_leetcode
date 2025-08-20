# Sqrt(x)

## Problem
Given a non-negative integer `x`, return the square root of `x` rounded down to the nearest integer.  
The returned integer should be non-negative as well.

You must **not** use any built-in exponent function or operator.  
For example, do not use `pow(x, 0.5)` in C++ or `x ** 0.5` in Python.

### Examples

**Example 1:**
```
Input: x = 4
Output: 2
Explanation: The square root of 4 is 2, so we return 2.
```

**Example 2:**
```
Input: x = 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since we round it down to the nearest integer, 2 is returned.
```

### Constraints
- `0 <= x <= 2^31 - 1`

---

## Solution 1: Linear Search (O(√x))
```cpp
class Solution {
public:
    int mySqrt(int x) {
        if (x < 2) return x;
        long long i = 1;
        while (i * i <= x) {
            i++;
        }
        return i - 1;
    }
};
```
✅ Simple but inefficient for large numbers.

---

## Solution 2: Binary Search (O(log x)) - Optimal
```cpp
class Solution {
public:
    int mySqrt(int x) {
        if (x < 2) return x;

        long long left = 1, right = x / 2;
        int ans = 0;

        while (left <= right) {
            long long mid = left + (right - left) / 2;
            if (mid * mid == x) {
                return mid;
            } else if (mid * mid < x) {
                ans = mid;      
                left = mid + 1; 
            } else {
                right = mid - 1;
            }
        }
        return ans;
    }
};
```
✅ Efficient, runs in logarithmic time.  
✅ Handles very large inputs up to 2^31 - 1.  
✅ Preferred approach for interviews and competitive programming.

---

## Complexity Analysis
- **Linear Search:** O(√x)
- **Binary Search:** O(log x) (better for large values)

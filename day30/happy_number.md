# Happy Number

## Problem Statement

Write an algorithm to determine if a number `n` is a **happy number**.

A **happy number** is defined by the following process: - Starting with
any positive integer, replace the number by the sum of the squares of
its digits. - Repeat the process until the number equals `1` (where it
will stay), or it loops endlessly in a cycle which does not include
`1`. - Those numbers for which this process ends in `1` are happy.

Return `true` if `n` is a happy number, and `false` if not.

------------------------------------------------------------------------

## Examples

**Example 1:**

    Input: n = 19
    Output: true
    Explanation:
    1² + 9² = 82  
    8² + 2² = 68  
    6² + 8² = 100  
    1² + 0² + 0² = 1  

**Example 2:**

    Input: n = 2
    Output: false

------------------------------------------------------------------------

## Constraints

-   1 \<= n \<= 2³¹ - 1

------------------------------------------------------------------------

## C++ Implementation

``` cpp
class Solution {
public:
    int getNext(int n) {
        int total = 0;
        while (n > 0) {
            int d = n % 10;
            total += d * d;
            n /= 10;
        }
        return total;
    }

    bool isHappy(int n) {
        if (n == 1) return true;   // happy number condition
        if (n == 4) return false;  // detects cycle (unhappy case)
        return isHappy(getNext(n));
    }
};
```

------------------------------------------------------------------------

## Explanation

-   The helper function `getNext(int n)` computes the sum of the squares
    of digits of `n`.
-   The recursive function `isHappy(int n)`:
    -   Returns `true` if the number becomes `1`.
    -   Returns `false` if the number reaches `4` (since all unhappy
        numbers eventually loop into `4`).
    -   Otherwise, it recursively checks the next number.

------------------------------------------------------------------------

✅ This solution efficiently detects whether a number is happy without
storing visited states, by leveraging the mathematical fact that all
unhappy numbers eventually enter a cycle containing `4`.

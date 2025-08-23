# Pascal's Triangle

## Problem Statement
Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it.

---

## Examples

### Example 1:
**Input:**
```
numRows = 5
```
**Output:**
```
[[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

### Example 2:
**Input:**
```
numRows = 1
```
**Output:**
```
[[1]]
```

---

## Constraints
- `1 <= numRows <= 30`

---

## C++ Solution

```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> result={{1},{1,1}};
        if(numRows==0) return {{}};
        if(numRows==1) return {{1}};
        if(numRows==2) return result;
        vector<int> row;
        vector<int> prevrow={1,1};
        for(int i = 3 ; i<=numRows;i++)
        {
            row.push_back(1);
            for(int i=0;i<prevrow.size()-1;i++)
            {
                row.push_back(prevrow[i]+prevrow[i+1]);
            }
            row.push_back(1);
            result.push_back({row});
            prevrow=row;
            row={};
        }
        return result;
    }
};
```

---

## Explanation
- The first row is always `[1]`.
- The second row is `[1,1]`.
- From the third row onwards:
  - Start with `1`.
  - Each middle element is the sum of two adjacent numbers from the previous row.
  - End with `1`.

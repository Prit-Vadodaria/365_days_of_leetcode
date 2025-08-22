# Symmetric Tree

## Problem Statement
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

---

## Examples

**Example 1:**

```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**Example 2:**

```
Input: root = [1,2,2,null,3,null,3]
Output: false
```

---

## Constraints
- The number of nodes in the tree is in the range [1, 1000].
- `-100 <= Node.val <= 100`

---

## Approach
We use a recursive helper function `isMirror` to check if two trees are mirrors of each other.  
- If both nodes are `NULL`, return `true`.  
- If one is `NULL` and the other is not, return `false`.  
- Otherwise, check:  
  - Values of the nodes are equal  
  - Left subtree of one is a mirror of the right subtree of the other  
  - Right subtree of one is a mirror of the left subtree of the other  

---

## Solution (C++)

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isMirror(TreeNode* p, TreeNode* q) {
        if (!p && !q) return true;
        if (!p || !q) return false;
        return (p->val == q->val) 
               && isMirror(p->left, q->right) 
               && isMirror(p->right, q->left);
    }

    bool isSymmetric(TreeNode* root) {
        if (!root->left && !root->right) return true;
        if (!root->left || !root->right) return false;
        return isMirror(root->left, root->right);
    }
};
```

---

✅ Time Complexity: **O(n)** (each node is visited once)  
✅ Space Complexity: **O(h)** (recursion stack, where `h` is tree height)  

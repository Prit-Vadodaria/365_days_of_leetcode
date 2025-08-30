
# Kth Smallest Element in a BST

## Problem Statement
Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.

### Example 1:
**Input:** root = [3,1,4,null,2], k = 1  
**Output:** 1  

### Example 2:
**Input:** root = [5,3,6,2,4,null,null,1], k = 3  
**Output:** 3  

### Constraints:
- The number of nodes in the tree is n.  
- 1 <= k <= n <= 10^4  
- 0 <= Node.val <= 10^4  

---

## C++ Solution

```cpp
#include <bits/stdc++.h>
using namespace std;

// Definition for a binary tree node.
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode() : val(0), left(nullptr), right(nullptr) {}
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};

class Solution {
public:
    vector<int> tree;
    void inordertravers(TreeNode* node) {
        if(!node) return;
        inordertravers(node->left);
        tree.push_back(node->val);
        inordertravers(node->right);
    }

    int kthSmallest(TreeNode* root, int k) {
        inordertravers(root);
        return tree[k-1];
    }
};
```

---

## Explanation
We perform an **inorder traversal** of the BST, which gives values in sorted order.  
The kth smallest element will be the (k-1)th index of this inorder traversal array.

# Binary Tree Inorder Traversal

## Problem Statement

Given the root of a binary tree, return the inorder traversal of its
nodes' values.

------------------------------------------------------------------------

## Examples

**Example 1:**

    Input: root = [1,null,2,3]
    Output: [1,3,2]

**Example 2:**

    Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]
    Output: [4,2,6,5,7,1,3,9,8]

**Example 3:**

    Input: root = []
    Output: []

**Example 4:**

    Input: root = [1]
    Output: [1]

------------------------------------------------------------------------

## Constraints

-   The number of nodes in the tree is in the range `[0, 100]`.
-   `-100 <= Node.val <= 100`

------------------------------------------------------------------------

## Solution (C++)

``` cpp
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
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> result;
        inorder(root, result);
        return result;
    }
    
    void inorder(TreeNode* node, vector<int>& res) {
        if (!node) return;
        inorder(node->left, res);
        res.push_back(node->val);
        inorder(node->right, res);
    }
};
```

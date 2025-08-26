# Binary Tree Traversals

This document contains the **Postorder** and **Preorder** traversal implementations for binary trees in C++.

---

## Postorder Traversal

### Problem Statement
Given the root of a binary tree, return the postorder traversal of its nodes' values.

**Example 1**  
Input: `root = [1,null,2,3]`  
Output: `[3,2,1]`  

**Example 2**  
Input: `root = []`  
Output: `[]`  

### Constraints
- Number of nodes in the tree is in the range `[0, 100]`  
- `-100 <= Node.val <= 100`  

### C++ Implementation For Postorder Traversal
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
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> result;
        postorder(root,result);
        return result;
    }
    void postorder(TreeNode* node,vector<int> &res)
    {
        if(!node) return;
        postorder(node->left,res);
        postorder(node->right,res);
        res.push_back(node->val);
    }
};
```
### C++ Implementation For Preorder Traversal
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
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> result;
        preorder(root,result);
        return result;
    }
    void preorder(TreeNode* node,vector<int> &res)
    {
        if(!node) return;
        res.push_back(node->val);
        preorder(node->left,res);
        preorder(node->right,res);
    }
};
```

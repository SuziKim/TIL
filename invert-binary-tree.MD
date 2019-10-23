## Invert Binary Tree @ LeetCode

<https://leetcode.com/problems/invert-binary-tree/>

---
### 1st Approach

```C++/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if (root == nullptr) {
            return root;
        }
        
        TreeNode *temp = invertTree(root->left);
        root->left = invertTree(root->right);
        root->right = temp;
        
        return root;
    }
};
```

---
### 2nd Approach

- Iterative solution: Use queue

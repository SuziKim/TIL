## Symmetric Tree @ LeetCode

<https://leetcode.com/problems/symmetric-tree/>

---
### 1st Approach (Recursive)

```C++
/**
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
    bool areMirrored(TreeNode* ltree, TreeNode* rtree) {
        if (ltree == nullptr && rtree == nullptr) {
            return true;
        }
        
        if (ltree == nullptr || rtree == nullptr) {
            return false;
        }
        
        if (ltree->val != rtree->val) {
            return false;
        }
        
        return areMirrored(ltree->left, rtree->right) && areMirrored(ltree->right, rtree->left);
    }
    
    bool isSymmetric(TreeNode* root) {
        if (root == nullptr) {
            return true;
        }
        
        return areMirrored(root->left, root->right);
    }
};
```

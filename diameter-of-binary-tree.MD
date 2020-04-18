### Diameter of Binary Tree (LeetCode)

<https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/529/week-2/3293/>

---

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
    int diameterOfBinaryTree(TreeNode* root) {
        helper(root);
        return FindMaxValue(root);
    }

public:
    int helper(TreeNode* root) {
        if (root == NULL) {
            return 0;
        }
        
        int left = helper(root->left);
        int right = helper(root->right);
        root->val = left + right;
        
        return max(left, right) + 1;
    }
    
    int FindMaxValue(TreeNode* root) {
        if (root == NULL) {
            return 0;
        }
        
        int left = FindMaxValue(root->left);
        int right = FindMaxValue(root->right);
        left = max(left, right);
        
        return max(left, root->val);
    }
};
```

## Path Sum (LeetCode)

<https://leetcode.com/problems/path-sum/>

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
    bool hasPathSum(TreeNode* root, int sum) {
        if (root == nullptr) {
            return false;
        }
        
        if (root->left == nullptr && root->right == nullptr) {
            return sum == root->val;
        }
        
        int child_sum = sum - root->val;
        return hasPathSum(root->left, child_sum) || hasPathSum(root->right, child_sum);
    }
};
```

---
### 2nd Approach (Iterative)

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
    bool hasPathSum(TreeNode* root, int sum) {
        if (root == nullptr) {
            return false;
        }
        
        std::stack<TreeNode*> node_stack;
        node_stack.push(root);
        
        while(!node_stack.empty()) {
            TreeNode* item = node_stack.top();
            node_stack.pop();
            
            if (item->left == nullptr && item->right == nullptr) {
                if (item->val == sum) {
                    return true;
                }
            }
            
            if (item->left != nullptr) {
                item->left->val += item->val;
                node_stack.push(item->left);
            }
            
            if (item->right != nullptr) {
                item->right->val += item->val;
                node_stack.push(item->right);
            }
        }
        
        return false;
    }
};
```

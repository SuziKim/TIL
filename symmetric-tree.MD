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
    bool isSymmetric(TreeNode* root) {
        if (root == nullptr) {
            return true;
        }
        
        std::queue<TreeNode*> node_queue;
        node_queue.push(root->left);
        node_queue.push(root->right);
        
        while (!node_queue.empty()) {
            auto left = node_queue.front();
            node_queue.pop();
            auto right = node_queue.front();
            node_queue.pop();
            
            if (left == nullptr && right == nullptr) {
                continue;
            }
            if (left == nullptr || right == nullptr) {
                return false;
            }
            
            if (left->val != right->val) {
                return false;
            }
            
            node_queue.push(left->left);
            node_queue.push(right->right);
            node_queue.push(left->right);
            node_queue.push(right->left);
        }
        
        return true;
    }
};
```

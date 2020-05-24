### Construct Binary Search Tree from Preorder Traversal

<https://leetcode.com/explore/challenge/card/may-leetcoding-challenge/537/week-4-may-22nd-may-28th/3339/>

---

1.

```C++
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
    TreeNode* bstFromPreorder(vector<int>& preorder) {
        TreeNode* bst = NULL;
        for (int value: preorder) {
            insertToBst(bst, value);
        }
        return bst;
    }

private:
    void insertToBst(TreeNode*& tree, int value) {
        TreeNode* item = (TreeNode*)malloc(sizeof(TreeNode));
        item->val = value;
        item->left = NULL;
        item->right = NULL;
        
        if (!tree) {
            tree = item;
        } else {
            TreeNode* ptr = tree;
            while (1) {
                if (item->val < ptr->val) {
                    if (ptr->left == NULL) {
                        ptr->left = item;
                        break;
                    } else {
                        ptr = ptr->left;
                    }
                } else {
                    if (ptr->right == NULL) {
                        ptr->right = item;
                        break;
                    } else {
                        ptr = ptr->right;
                    }
                }
            }
        }
        
    }
};
```

2.

```C++
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
    TreeNode* bstFromPreorder(vector<int>& preorder) {
        TreeNode* bst = NULL;
        for (int value: preorder) {
            bst = insertToBst(bst, value);
        }
        return bst;
    }

private:
    TreeNode* insertToBst(TreeNode* tree, int val) {
        if (!tree) {
            TreeNode* item = new TreeNode(val);
            return item;
        }
        
        if (val < tree->val) {
            tree->left = insertToBst(tree->left, val);
        } else {
            tree->right = insertToBst(tree->right, val);
        }
        return tree;
    }
};
```

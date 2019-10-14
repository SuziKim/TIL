## Merge Two Sorted Lists @ LeetCode

<https://leetcode.com/problems/merge-two-sorted-lists/>
---
### 1st Approach

```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if (l1 == nullptr) {
            return l2;
        }
        if (l2 == nullptr) {
            return l1;
        }
        
        ListNode *merged = nullptr;
        ListNode *merged_tail = nullptr;
        
        while (l1 != nullptr && l2 != nullptr) {
            if (l1->val < l2->val) {
                if (merged_tail == nullptr) {
                    merged_tail = l1;
                } else {
                    merged_tail->next = l1;
                    merged_tail = merged_tail->next;
                }
                l1 = l1->next;
            } else {
                if (merged_tail == nullptr) {
                    merged_tail = l2;
                } else {
                    merged_tail->next = l2;
                    merged_tail = merged_tail->next;
                }
                l2 = l2->next;
            }
            if (merged == nullptr) {
                merged = merged_tail;
            }
        }
        
        if (l1 != nullptr) {
            merged_tail->next = l1;
        } else if (l2 != nullptr) {
            merged_tail->next = l2;
        }
        
        return merged;
    }
};
```


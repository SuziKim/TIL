## Remove Nth Node From End of List @ LeetCode

<https://leetcode.com/problems/remove-nth-node-from-end-of-list/>

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if (head == nullptr) {
            return nullptr;
        }
        
        ListNode *node_pt = head;
        int count = 1;
        while (node_pt->next != nullptr) {
            node_pt = node_pt->next;
            count++;
        }
        
        node_pt = head;
        if (count == n) {
            head = head->next;
            delete(node_pt);
            return head;
        }
        
        for (int i = 1; i < count - n; ++i) {
            node_pt = node_pt->next;
        }
        
        ListNode *target = node_pt->next;
        if (target != nullptr) {
            node_pt->next = target->next;
            delete(target);
        } else {
            node_pt->next = nullptr;
        }
        
        return head;
    }
};
```

---
### 2nd Approach

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if (head == nullptr) {
            return head;
        }
        
        ListNode dummy(0);
        dummy.next = head;
        
        ListNode *fast = &dummy;
        ListNode *slow = &dummy;
        
        for (int i = 0; i < n; ++i) {
            fast = fast->next;
        }
        
        while (fast->next != nullptr) {
            fast = fast->next;
            slow = slow->next;
        }
        
        ListNode *target = slow->next;
        slow->next = target->next;
        delete (target);
        
        return dummy.next;
    }
};
```

## Reverse Linked List @ LeetCode

<https://leetcode.com/problems/reverse-linked-list>

---
### 1st Approach (Iterative)

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
    ListNode* reverseList(ListNode* head) {
        ListNode *reversed = nullptr;
        
        while (head != nullptr) {
            ListNode *item = head;
            head = head->next;
            item->next = reversed;
            reversed = item;
        }
        
        return reversed;
    }
};
```

---
### 2nd Approach (Recursive)

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
    ListNode* reverseList(ListNode* head) {
        if (head == nullptr) 
            return head;
        if (head->next == nullptr) 
            return head;
        
        ListNode* reversed = reverseList(head->next);
        head->next->next = head;
        head->next = nullptr;
        
        return reversed;
    }
};
```

- `head->next->next = head;`

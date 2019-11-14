## Intersection of Two Linked Lists (LeetCode)

<https://leetcode.com/problems/intersection-of-two-linked-lists/>

---
### Observations

- Make cycle by connecting tail to the other list's head.

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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if (headA == nullptr || headB == nullptr) {
            return nullptr;
        }
        
        ListNode *pA = headA;
        ListNode *pB = headB;
        
        int countA = 0, countB = 0;
        while (countA < 2 && countB < 2) {
            if (pA == nullptr) {
                pA = headB;
                countA++;
            }
            if (pB == nullptr) {
                pB = headA;
                countB++;
            }
            
            if (pA == pB) {
                return pA;
            }
            
            pA = pA->next;
            pB = pB->next;
        }
        
        return nullptr;
    }
};
```

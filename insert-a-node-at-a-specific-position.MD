### Insert a node at a specific position in a linked list

---

<https://www.hackerrank.com/challenges/insert-a-node-at-a-specific-position-in-a-linked-list>

```C++
// Complete the insertNodeAtPosition function below.

/*
 * For your reference:
 *
 * SinglyLinkedListNode {
 *     int data;
 *     SinglyLinkedListNode* next;
 * };
 *
 */
SinglyLinkedListNode* insertNodeAtPosition(SinglyLinkedListNode* head, int data, int position) {
    SinglyLinkedListNode* item = (SinglyLinkedListNode*)malloc(sizeof(SinglyLinkedListNode));
    item->data = data;
    SinglyLinkedListNode* ptr = head;
    for (int i = 1; i < position; ++i) {
        ptr = ptr->next;
    }
    item->next = ptr->next;
    ptr->next = item;
    return head;
}
```

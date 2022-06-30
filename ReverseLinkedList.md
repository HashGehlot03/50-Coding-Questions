[Problem Statement](https://leetcode.com/problems/reverse-linked-list/)

```cpp
// Time Complexity - O(N)             Space Complexity - O(1)
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if (head == NULL)
            return NULL;
        if (head->next == NULL)
            return head;
        // Previous pointer
        ListNode *previous = head;
        // Current pointer
        ListNode *curr = head->next;
        head->next = NULL;
        while (curr->next) {
            ListNode *next = curr->next;
            curr->next = previous;
            previous = curr;
            curr = next;
        }
        curr->next = previous;
        return curr;
    }
};
```

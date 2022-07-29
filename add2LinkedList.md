[Problem Statement](https://leetcode.com/problems/add-two-numbers/)

## Approach :- In this approach, we'll iterate through nodes from each linked list(correspondingly) and calculate sum and carry and further assign it to next node.

```cpp
// Time Complexity - O(max(N,M))          Space Complexity - O(N)
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *dummy = new ListNode();
        ListNode *temp = dummy;
        int carry = 0;
        while(l1!=nullptr || l2!=nullptr || carry)
        {
            int sum = 0;
            if(l1!=nullptr)
            {
                sum+=l1->val;
                l1 = l1->next;
            }
            if(l2!=nullptr)
            {
                sum+=l2->val;
                l2 = l2->next;
            }
            sum+=carry;
            carry = sum/10;
            ListNode *node = new ListNode(sum%10);
            temp->next = node;
            temp = temp->next;
        }
        return dummy->next;
    }
};
```

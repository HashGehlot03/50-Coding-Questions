[Problem Statement](https://leetcode.com/problems/add-two-numbers/)

## Approach :- In this approach, we'll iterate the node by node of both linked list and maintains the resultant sum's last digit and carry as well. Then pushing the nodes in the newly created output linked list.

```cpp
// Time Complexity - O(N)           Space Complexity - TBUN
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *ans = new ListNode(0);
        ListNode *p = l1, *q=l2, *curr = ans;
        int carry=0;
        while(p!=NULL || q!=NULL){
            int x = (p!=NULL) ? p->val : 0;
            int y = (q!=NULL) ? q->val : 0;
            int sum = carry + x+ y;
            carry = sum/10;
            curr->next = new ListNode(sum%10);
            curr = curr->next;
            if(p!=NULL) p = p->next;
            if(q!=NULL) q = q->next;
        }
        if(carry>0){
            curr->next = new ListNode(carry);
        }
        return ans->next;
    }
};
```

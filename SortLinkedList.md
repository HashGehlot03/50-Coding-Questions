[Problem Statement](https://leetcode.com/problems/sort-list/)

## Approach 1 :- Bubble sort the sort linked list.

```cpp
// Time Complexity - O(N^2)           Space Complexity - O(1)
class Solution {
public:
    ListNode* sortList(ListNode* head) {
        ListNode* i = head;
        while(i){
        ListNode* j = head;
        while(j->next){
            if(j->val > j->next->val){
                int temp = j->val;
                j->val = j->next->val;
                j->next->val = temp;
            }
            j = j->next;
        }
        i = i->next;
    }
    return head;
    }
    
};
```

## Approach 2 :- Merge sort the linked list. In merge sort of linked list, for breaking in 2 halves, we iterate the linked list using slow and fast pointer upto middle and then assign slow->next to null and create new head of slow->next.

```cpp
// Time Complexity - O(NlogN)      logN is finding middle and working on half everytime and n for searching.   Space Complexity - O(logN)
class Solution {
public:
    ListNode* mergeSortedLists(ListNode* head1, ListNode* head2){
      ListNode* ptr1 = head1;
      ListNode* ptr2 = head2;
      ListNode* returnedHead = NULL;
      ListNode* tail = NULL;
      ListNode* lower;
      while(ptr1 || ptr2){
        if(ptr1 && ptr2){
          if(ptr1->val < ptr2->val){
            lower = ptr1;
            ptr1 = ptr1->next;
          }else{
            lower = ptr2;
            ptr2 = ptr2->next;
          }
        }else if(ptr1){
          lower = ptr1;
          ptr1 = ptr1->next;
        }else{
          lower = ptr2;
          ptr2 = ptr2->next;
        }
        if(returnedHead == NULL){
          returnedHead = lower;
          tail = lower;
        }else{
          tail->next = lower;
          tail = tail->next;
        }
      }
      return returnedHead;
}

ListNode* mergeSort(ListNode* head){
  if(head == NULL || head->next == NULL) return head;
  ListNode* slow = head;
  ListNode* fast = head;
  while(fast->next && fast->next->next){
    slow = slow->next;
    fast = fast->next->next;
  }
  ListNode* headRightHalf = slow->next;
  slow->next = NULL;
  head = mergeSort(head);
  headRightHalf = mergeSort(headRightHalf);
  return mergeSortedLists(head, headRightHalf);
}
    ListNode* sortList(ListNode* head) {
        return mergeSort(head);
        
    }
    
};
```

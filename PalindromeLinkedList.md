[Problem Statement](https://leetcode.com/problems/palindrome-linked-list/)

Prerequisite :- For this problem we should also know reverse of a linked list, finding middle of a linked list.

## Approach 1 :- Simply traverse the list and push the elements in vector and then check that array is palindrome or not.

```cpp
// Time Complexity - O(N)      Space Complexity - O(N)
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        vector<int> arr;
        int start = 0;
        ListNode* curr = head;
        while(curr)
        {
            arr.push_back(curr->val);
            curr = curr->next;
        }
        int end = arr.size()-1;
        
        // This below approach can also be applicable in checking for palindrome in array or string
        while(start<=end)
        {
            if(arr[start] == arr[end])
            {
                start++;
                end--;
            }
            else return false;
        }
        return true;
        
    }
};
```

## Approach 2 [Optimized] :- In this approach, Use slow and fast pointer to reach to middle point, when we reaches middle point then reverse the remaining list after mid. Now compare the both halves using both pointer and check for equality of elements.

```cpp
// Time Complexity - O(N)            Space Complexity - O(1)
class Solution {
public:
    ListNode* getMid(ListNode* head){
        ListNode* slow = head;
        ListNode* fast = head->next;
        while(fast!=NULL && fast->next!=NULL)
        {
            fast = fast->next->next;
            slow = slow->next;
        }
        return slow;
    }
    ListNode* reverse(ListNode* head){
        ListNode* curr = head;
        ListNode* prev = NULL;
        ListNode* next = NULL;
        while(curr!=NULL)
        {
            next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
    bool isPalindrome(ListNode* head){
        if(head == NULL || head->next == NULL) return true;
        ListNode* mid = getMid(head);   // Get middle node
        ListNode* temp = mid->next;     // We have to reverse after the middle element
        mid->next = reverse(temp);   // Now reverse the other half
        ListNode* head1 = head;
        ListNode* head2 = mid->next;
        while(head2!=NULL)
        {
            if(head1->val != head2->val){
                return false;
            }
            head1 = head1->next;
            head2 = head2->next;
            
        }
        temp = mid->next;
        mid->next = reverse(temp);
        return true;
    }
};
```


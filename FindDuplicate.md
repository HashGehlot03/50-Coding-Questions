[Problem Statement](https://leetcode.com/problems/find-the-duplicate-number/)


## Approach 1[Extra space] :- In this approach, we can use unordered set in which we can store element in set by checking its existence, if it exists then occur again through iteration, it is duplicate, return the element.

```cpp
// Time Complexity - O(N)         Space Complexity - O(N)
class Solution {
public:
        int findDuplicate(vector<int>& nums){
            int n = nums.size();
            unordered_set<int> st;
            for(int i=0;i<n;i++){
                if(st.find(nums[i])!=st.end()) return nums[i];
                st.insert(nums[i]);
            }
        }
        
}

```

## Approach 2 :- In this approach, first we'll sort the array then iterate it and compare the element with its next, if they are equal means they are duplicate.

```cpp
// Time Complexity - O(N)            Space Complexity - O(1)
class Solution {
public:
        int findDuplicate(vector<int>& nums){
            int n = nums.size();
            sort(nums.begin(),nums.end());
            for(int i=0;i<n-1;i++) {
                if(nums[i] == nums[i+1]) return nums[i];
            }
            return -1;
        }
}
```

## Approach 3[Floyd's tortoise and hare algorithm] :- In this we'll use two pointer i.e. slow and fast.Slow pointer iterate by one and fast pointer iterates by two.So we'll move both pointer until both pointer's value is equal.After equality condition, reassign fast to beginning then iterate slow and fast by one, and the point where they meet is the duplicate one.


```cpp
// Time Complexity - O(N)    Complexity - O(1)
class Solution {
public:
        int findDuplicate(vector<int>& nums){
            int n = nums.size();
            int fast = nums[0];
            int slow = nums[0];
            do {
                slow = nums[slow];
                fast = nums[nums[fast]];
            } while(slow!=fast)
            
            fast = nums[0];
            while(slow!=fast)
            {
                slow = nums[slow];
                fast = nums[fast];
            }
            return slow;
        }
}
```

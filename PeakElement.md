[Problem Statement](https://leetcode.com/problems/find-peak-element/)

## Approach 1 [Brute Force] :- In this approach ,we simply first check the edge conditions(at beginning and end of array)
- If array has one element then it is itself a peak.
- If array has two element then we'll compare both. Element which is greater is a peak.
- For other conditions, we check its +1 and -1 element ,if they are smaller therefore element is peak

```cpp
// Time Complexity - O(N)               Space Complexity - O(1)
class Solution {
public:
    int findPeakElement(vector<int>& nums){
        int n = nums.size();
        if(n==1) return 0;
        else if(n==2)
        {
            int peak = (nums[0] >= nums[1]) ? 0 : 1;
            return peak;
        }
        else
        {
            if(nums[0]>=nums[1]) return 0;
            if(nums[n-1]>=nums[n-2]) return n-1;
            
            for(int i=1;i<n-1;i++)
            {
                if(nums[i]>=nums[i-1] && nums[i]>=nums[i+1])
                {
                    return i;
                }
            }
        }
        return -1;
    }
};
```

## Approach 2[Binary Search] :- Here first we check the edge conditions(at beginning and at end of array) and then other conditions.
- Algorithm for other condition - We check the element's next and its previous element.
1. If previous is greater, then we'll shift end pointer to m-1.
2. If next is greater, then we'll shift start pointer to m.


```cpp
// Time Complexity - O(logN)            Space Complexity - O(1)
class Solution {
public:
    int findPeakElement(vector<int>& nums){
        int n = nums.size();
        int start = 0;
        int end = nums.size() - 1;
        while(start<=end)
        {
            int mid = start + (end - start)/2;
            if((mid == 0 || nums[mid]>=nums[mid-1]) && (mid == n-1 || nums[mid]>=nums[mid+1])) return mid;
            else if(nums[mid]<=nums[mid+1]) start = mid+1;
            else end = mid-1;
        }
        return -1;
    }
};
```

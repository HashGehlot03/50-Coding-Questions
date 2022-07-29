[Problem Statement](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

## Approach 1 :- In this approach, we'll simply find the minimum of the array.

```cpp
class Solution{
public:
    int findMin(vector<int>& nums){
        int n = nums.size();
        int minElement = INT_MAX;
        for(int i:nums)
        {
            minElement = min(minElement,i);
        }
        return minElement;
   }
};
```

## Approach 2 [Binary Search] :- In this approach, we'll find the mid and shift to left part or right part according to following conditions.
E.g. {4,5,6,7,1,2,3}
We have two halves present in array ,first is rotated part (4,5,6,7) and other is unrotated part (1,2,3)

Conditions
- If nums[mid] is greater than nums[mid+1] return nums[mid+1]
- else if nums[mid-1] > nums[mid] return nums[mid]
- else if nums[mid] > nums[e] s = mid+1
- else e = mid-1

```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int start = 0;
        int end = nums.size()-1;
        if(nums[start] < nums[end]) return nums[start];
        while(start < end)
        {
            int mid = (start + end)/2;
            if(nums[mid+1] < nums[mid]) return nums[mid+1];
            else if(nums[mid-1] > nums[mid]) return nums[mid];
            else if(nums[mid] > nums[end]) start = mid+1;
            else end = mid-1;
        }
        return nums[start];
    }
};
```

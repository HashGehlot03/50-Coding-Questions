[Problem Statement](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

## Approach 1 :- Simply find minimum in the array.

```cpp
// Time Complexity - O(N)         Space Complexity - O(1)
class Solution {
public:
    int findMin(vector<int>& nums) {
        int min = INT_MAX;
        for(int i:nums)
        {
            if(i < min) min = i;
        }
        return min;
    }
};
```

## Approach 2 :- In this approach, we use binary search. Imagine an array as two part such that first part is that rotated half and another is unrotated part. Now we follow some conditions i.e.
- First find mid as binary search follows.
- Now if mid > mid+1, return mid+1.
- If mid-1 > mid, return mid.
- If mid > rightmost value then shift to unrotated half i.e. left = mid+1.
- else right = mid-1.

```cpp
// Time Complexity - O(logN)             Space Complexity - O(1)
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

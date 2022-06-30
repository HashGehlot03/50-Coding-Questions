[Problem Statement](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

## Approach 1 :- Problem is quite simple but it is represented hardly. We only require to find the maximum element. That element behind which each element is lesser(follow increasing order) and ahead of it follow the decreasing order.

```cpp
// Time Complexity - O(N)               Space Complexity - O(1)
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int m = INT_MIN;
        int ans = -1;
        for(int i=0;i<arr.size();i++){
            if(arr[i]>m)
            {
                ans = i;
                m = arr[i];
            }
        }
        return ans;
    }
};
```

## Approach 2 :- Same we are finding maximum but using max function.

```cpp
// Time Complexity - O(N)           Space Complexity - O(1)
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr){
        return max_element(arr.begin(),arr.end()) - arr.begin(); // ans is an iterator data type
    }
};
```

## Approach 3 [Binary Search] :- In this approach, we'll find mid element at every iteration and check its next element. 
- If mid element is greater than its next(means maybe mid element is greater),assign answer with mid and shift end to mid.
- If mid element is lesser than its next(means maybe mid's next element is greater),assign answer with mid+1 and shift start to mid+1.

```cpp
// Time Complexity - O(logN)          Space Complexity - O(1)
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr){
        int start = 0;
        int end = arr.size() - 1;
        int ans = -1;
        while(start<end)
        {
            int mid = start+(end-start)/2;  //finding mid point
            if(arr[mid] > arr[mid+1])  // m maybe largest
            {
                ans = mid;
                end = mid;
            }
            else             // m+1 maybe largest
            {
                ans = mid+1;
                start = mid+1;
            }
        }
        return ans;
    }
};
```

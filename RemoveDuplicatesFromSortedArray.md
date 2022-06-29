[Problem Statement](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Approach 1[Extra Space] :- In this approach we'll use extra array (temp) in which we store all the unique elements of original array and return the array

```cpp
class Solution {
public:
        int removeDuplicates(vector<int>& nums){
        vector<int> temp;
        int n = nums.size();
        int j=0;  //Trace the indices in temp array
        for(int i=0;i<n-1;i++){
            if(arr[i]!=arr[i+1]) temp.push_back(arr[i]);
        }
        temp.push_back(arr[n-1]);
        return temp;
    }
}
```
## Approach 2[Inplace] :- We'll use two pointer approach in which i is at some element and j is at its next. Now check i's and j's value. If they are equal increment j otherwise increment i and assign j's value to ith position.

```cpp
// Time Complexity - O(N)        Space Complexity - O(1)
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int n = nums.size();
        if(n == 0) return 0;
        int i = 0;
        for(int j=1;j<n;j++){
            if(nums[i]!=nums[j]){
                i++;
                nums[i] = nums[j];
            }
        }
        return i+1;
        
    }
};
```

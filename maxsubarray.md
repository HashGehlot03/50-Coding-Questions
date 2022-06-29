[Problem Statement](https://leetcode.com/problems/maximum-subarray/)

## Approach 1 :- Brute force approach - First we'll iterate the elements and its subarray with nested loops and another nested inside to calculate the sum of the subarrays and finds it maximum.

```cpp
//Time complexity - O(N^3)           Space Complexity - O(N)
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int maximum = INT_MIN;
        for(int i=0;i<n;i++){
            for(int j=i;j<n;j++){
                int sum = 0;
                for(int k=i;k<=j;k++){
                    sum += nums[k];
                }
                if(sum > maximum) maximum = sum;
            }
        }
        return maximum;
    }
};
```

## Approach 2 :- [Kadane's algorithm](https://medium.com/@rsinghal757/kadanes-algorithm-dynamic-programming-how-and-why-does-it-work-3fd8849ed73d)

```cpp
// Time complexity - O(N)      Space Complexity - O(1)
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int maximum = INT_MIN;
        int current_sum = 0;
        for(int i=0;i<n;i++){
            current_sum = max(current_sum + nums[i],nums[i]);
            maximum = max(current_sum,maximum);
        }
        
        return maximum;
    }
};
```

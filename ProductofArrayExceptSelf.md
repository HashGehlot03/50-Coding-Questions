[Problem Statement](https://leetcode.com/problems/product-of-array-except-self/)

## Approach 1 [Brute Force] :- In this approach, we'll iterate each element and calculate the product using nested for loop.

```cpp
// Time Complexity - O(N^2)         Space Complexity - O(N)
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> res;
        for(int i=0;i<n;i++)
        {
            int product = 1;
            for(int j=0;j<n;j++)
            {
                if(i == j) continue;
                else product*=nums[j];
            }
            res.push_back(product);
        }
        return res;
    }
};
```


## Approach 2 [Optimized] :- In this approach, we'll calcualte array of cumulativeFromLeft and cumulativeFromRight.
- cumulativeFromLeft : 1) assign cumulativeFromLeft[0][0] = 1
                       2) cumulativeFromLeft[i] = cumulativeFromLeft[i-1] * nums[i-1]; i++
- cumulativeFromRight: 1) assign cumulativeFromRight[n-1] = 1;
                       2) cumulativeFromRight[i] = cumulativeFromRight[i+1] + arr[i+1]; i--

Now multiply both array's corresponding element
  

```cpp
// Time Complexity - O(N)          Space Complexity - O(1)
class Solution {
public:
    vector<int> productExceptSelf(vector<int> nums){
          int n = nums.size();
          int cumulativeFromLeft[n];
          cumulativeFromLeft[0] = 1;
          for(int i = 1; i < n; i++)
            cumulativeFromLeft[i] = cumulativeFromLeft[i-1] * nums[i-1];

          int cumulativeFromRight[n];
          cumulativeFromRight[n-1] = 1;
          for(int i = n-2; i >= 0; i--)
            cumulativeFromRight[i] = cumulativeFromRight[i+1] * nums[i+1];

          vector<int> output;
          for(int i = 0; i < n; i++)
            output.push_back(cumulativeFromLeft[i] * cumulativeFromRight[i]);

          return output;
    }
};
```

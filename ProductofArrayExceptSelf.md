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

## Approach 2 

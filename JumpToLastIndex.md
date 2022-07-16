[Problem Statement](https://leetcode.com/problems/jump-game/)

## Approach 1 :- Recursive approach (unable to understand) 😞

```cpp
Time Complexity - O(2^N)           Space Complexity - O(N)
class Solution {
public:
     bool canJump(vector<int>& nums,int i=0) {
         if(i == nums.size()-1) return true;
         for(int j=1;j<=nums[j];j++)
         {
             if(canJump(nums,i+j)) return true;
         }
         return false;
        
     }
};
```

## Approach 2 [Dynamic Programming] :- In this approach we'll use an array of booleans dp, where each element dp[i] says if there is a way to reach the index i, then at the end, if the last element of the array is true, it means that we can reach the index.
- Set the first cell of dp true.
- Iterate the array, and set the number of cells in dp  to true (number of cells are the numbers that we encounter during iteration of array)

```cpp
// Time Complexity - O(N^2)         Space Complexity - O(N)
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int n = nums.size();
        bool dp[n];
        for(int i=0;i<n;i++) dp[i] = false;
        dp[0] = true;
        for(int i=0;i<n;i++)
        {
            if(!dp[i]) return false;
            else if(i+nums[i] >= n-1) return true;
            else
            {
                for(int j=1;j<=nums[i];j++)
                {
                    dp[i+j] = true;
                }
            }
        }
        return dp[n-1];
        
    }
};
```

## Approach 3 [Optimized] :- In this approach, we'll keep track of max index at every iteration. We calculate maxIndex by adding index with array[index].
If index becomes greater than maxIndex, it's not possible to reach the end otherwise we reach it.

```cpp
// Time Complexity - O(N)           Space Complexity - O(1)
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int maxIndex = 0;
        int n = nums.size();
        for(int i=0;i<n;i++)
        {
            if(i > maxIndex) return false;
            maxIndex = max(maxIndex,i+nums[i]);
        }
        return maxIndex >= n-1;
        
     }
};
```


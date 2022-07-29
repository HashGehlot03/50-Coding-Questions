[Problem Statement](https://leetcode.com/problems/climbing-stairs/)

## Approach 1 [Recursion] :- In this approach, we'll recursively find the possible combinations of steps (n-steps) and eventually find the number of ways.

```cpp
// Time Complexity  O(M^N) where N is the number of steps and M is the size of possibleSteps     Space Complexity - O(N)
class Solution {
public:
    int climbStairs(int n) {
        vector<int> possibleSteps = {1,2};
        return numberOfWays(n,possibleSteps);
    }
    
    int numberOfWays(int n,vector<int>& possibleSteps){
        if(n==0) return 1;
        int nbWays = 0;
        for(int steps:possibleSteps)
        {
            if(n-steps >= 0)
                nbWays+=numberOfWays(n-steps,possibleSteps);
        }
        return nbWays;
    }
};
```

## Approach 2 [Dynamic Programming] :- In this approach, we'll create a new array of size (n+1) and assign its first value with 1. Now iterate the array and add the sum of (i-step[0]),(i-step[1]).... if they are positive.

```cpp
// Time Complexity - O(N^2)           Space Complexity - O(N)
class Solution {
public:
    int climbStairs(int n) {
        vector<int> possibleSteps = {1,2};
        return numberOfWays(n,possibleSteps);
    }
    
    int numberOfWays(int n,vector<int>& possibleSteps){
        int waysArray[n+1];
        waysArray[0] = 1;
        for(int i=1;i<n+1;i++)
        {
            int ways = 0;
            for(int step : possibleSteps)
            {
                if(i-step >= 0) ways += waysArray[i-step];
                
            }
            waysArray[i] = ways;
        }
        return waysArray[n];
    }
};
```

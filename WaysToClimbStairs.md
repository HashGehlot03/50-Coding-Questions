## Problem Statement :- Given a staircase of n steps and set of possible of steps that we can climb at a time named possibleSteps. Create a function that returns a number of ways that a person can take to reach the top of the staircase.

n = 5,  possibleSteps = [1,2]
Output = 8

1. 1,1,1,1,1
2. 1,1,1,2
3. 2,1,1,1
4. 1,2,1,1
5. 1,1,2,1
6. 1,2,2
7. 2,2,1
8. 2,1,2


### Approach 1 [Recursion] :- In this approach, we recursively start from top of stair(n) and check the way according to the steps given(n - step1, n-step2, n-step3 ......) and eventually calculate the ways.

```cpp
// Time Complexity - O(M^N)        Space Complexity - O(N)     Where M is the size of possibleSteps and N is the number of staircase given.
class Solution {
public:
    int climbStairs(int n) {
        vector<int> possibleSteps = {1,2};
        if(n == 0) return 1;
        int ways = 0;
        for(int i:possibleSteps)
        {
            if(n-i >= 0) ways += climbStairs(n-i);
        }
        return ways;
    }
};
```

### Approach 2 [DP] :- We'll create new array of size N+1 and assign first cell's value  is 1. Now iterate the array and fill the cell with sum of :-
       (i-step1 + i-step2 + i-step3 .......) if exist and at the end we get the number of ways.
       
```cpp
// Time Complexity - O(M*N)            Space Complexity - O(N)
class Solution {
public:
    int climbStairs(int n) {
        vector<int> possibleSteps = {1,2};
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

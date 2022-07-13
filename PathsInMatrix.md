[Problem Statement](https://leetcode.com/problems/unique-paths-ii/)
  
## Approach 1[Recursion] :- In this approach, we recursively reach to all cells and calculate the path if we reach to last cell. If we encounter wall (i.e. 1), we return 0;
  
```cpp
// Time Complexity - O(2^(N+M))        Space Complexity - O(N*M)
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid,int i=0,int j=0) {
        int m = obstacleGrid.size();
        int n = obstacleGrid[0].size();
        if(i > m-1 || j > n-1 || obstacleGrid[i][j] == 1) return 0;
        else if(i == m-1 && j == n-1) return 1;
        return uniquePathsWithObstacles(obstacleGrid,i+1,j) + uniquePathsWithObstacles(obstacleGrid,i,j+1);
        //return dp[m-1][n-1];
    }
};
```
In approach 1, we're repeating cells many times which is increaing time complexity. To overcome this,

## Approach 2 [DP] :- In this approach, we'll create a newly created matrix of size same as given obstacle. We'll fill the cells based on below conditions.
- For first cell, element is same as in given matrix.
- For first row, we check if given matrix has 1, so we assign 0 in created matrix otherwise previous row value (of created matrix) is assigned.
- For first column, we check if given matrix has 1, so we assign 0 in created matrix otherwise previous column value (of created matrix) is assigned.
- For remaining cell, we'll sum up the upward and backward value to current cell.

```cpp
// Time Complexity - O(N*M)            Space Complexity - O(N*M)
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>> obstacleGrid){
          int n = obstacleGrid.size();
          int m = obstacleGrid[0].size();
          int dp[n][m];
          dp[0][0] = obstacleGrid[0][0] == 1 ? 0 : 1;
          for(int i = 1; i < m; i++){
            if(obstacleGrid[0][i] == 1) dp[0][i] = 0;
            else dp[0][i] = dp[0][i-1];
          }
          for(int i = 1; i < n; i++){
            if(obstacleGrid[i][0] == 1) dp[i][0] = 0;
            else dp[i][0] = dp[i-1][0];
          }
          for(int i = 1; i < n; i++){
            for(int j = 1; j < m; j++){
              if(obstacleGrid[i][j] == 1) dp[i][j] = 0;
              else dp[i][j] = dp[i-1][j] + dp[i][j-1];
            }
          }
          return dp[n-1][m-1];
        }

};
```

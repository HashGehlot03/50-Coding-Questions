[Problem Statement](https://leetcode.com/problems/minimum-path-sum/)

## Approach 1[Brute Force] :- In this approach, we start with first cell and follows a path from two options i.e. towards row or towards column. The path we choose from where we get minimum cost path then we recursively goes with all options.

```cpp
// Time Complexity - O(2^(m + n))         Space Complexity - O(m+n)
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid,int i=0,int j=0) {
        int m = grid.size();
        int n = grid[0].size();
        if(i == m-1 && j == n-1) return grid[i][j];
        if(i == m-1) return grid[i][j] + minPathSum(grid,i,j+1);
        if(j == n-1) return grid[i][j] + minPathSum(grid,i+1,j);
        else return grid[i][j] + min(minPathSum(grid,i,j+1),minPathSum(grid,i+1,j));
    }
};
```

In the approach 1, we are repeating some cells in each recursion ,so to overcome this issue.

## Approach 2[Dynamic Programming] :- In this approach, we'll create a new matrix(named costs), where we calculate path at each cell and eventually we get the minimum cost path at bottom right cell.
- Initially we can fill the cell of first row and column easily.
- For first cell, matrix[0][0] is same.
- For first row, just add the previous and current element upto last.
- For first column, do the same upto last.
- Now fill the remaining cell by finding minimum cost from upward or backward.

```cpp
// Time Complexity - O(m*n)           Space Complexity - O(m*n)
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        int costs[m][n];
        costs[0][0] = grid[0][0];
        for(int i=1;i<n;i++)
        {
            costs[0][i] = costs[0][i-1] + grid[0][i];
        }
        for(int i=1;i<m;i++)
        {
            costs[i][0] = costs[i-1][0] + grid[i][0];
        }
        for(int i = 1; i < n; i++)
            for(int j = 1; j < m; j++)
                costs[i][j] = min(costs[i-1][j], costs[i][j-1]) + grid[i][j];
        
        return costs[m-1][n-1];
    }
};
```

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
        // //Fast I/O in C++
        // ios_base::sync_with_stdio(false);
        // cin.tie(NULL);
        
        int rows = grid.size();
        if(rows==0)
            return 0;
        int cols = grid[0].size();
        vector<vector<int>> costs(rows,vector<int>(cols,0));
        int i,j;
        
        costs[0][0] = grid[0][0];  //1st element is starting point
        //Fill 1st row
        for(i=1;i<cols;++i)
            costs[0][i] = costs[0][i-1] + grid[0][i];
        
        //Fill 1st Col
        for(i=1;i<rows;++i)
            costs[i][0] = costs[i-1][0] + grid[i][0];
        
        //Now fill the rest of the cell
        for(i=1;i<rows;++i)
        {
            for(j=1;j<cols;++j)
                costs[i][j] = grid[i][j] + min(costs[i-1][j],costs[i][j-1]);
        }
        return costs[rows-1][cols-1];
    }
};
```

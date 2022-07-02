[Problem Statement](https://leetcode.com/problems/longest-palindromic-substring/)

## Approach 1[Brute Force] :- In this, first we find all substrings (as same as subarrays) which takes O(N^2) time and then check substring for palindrome and keeping up with its length(as well as maximum).

```cpp
// Time Complexity - O(N^3)           Space Complexity - O(N)
class Solution {
public:
    bool isPalindrome(string s)  // We can also create isPalindrome function using start and end index,and check if they are equal or not. if not return false.
    {
        string rev = s;
        reverse(rev.begin(),rev.end());
        return s == rev;
    }
    string longestPalindrome(string s) {
        int n = s.length();
        int best_len = 0;
        string best_s = "";
        for(int i=0;i<n;i++)
        {
            for(int j=i;j<n;j++)
            {
                int len = j-i+1;
                string subs = s.substr(i,len);
                if(isPalindrome(subs) && len > best_len)
                {
                    best_len = len;
                    best_s = subs;
                }
            }
        }
        return best_s;
    }
};
```

## Approach 2[Expand from center] :- In this approach, here we iterate element and check its neighbours, it both neighbours are equal we can consider it a palindrome and further goes with further neighbours and check for palindrome.
- In case of odd length, center is one element.
- In case of even length, center is two element.

```cpp
// Time Complexity - O(N^2)           Space Complexity - O(1)
class Solution {
public:
    string longestPalindrome(string s) {
        int n = s.size();
        if(n < 2) return s;
        int max_len = 1;
        int start = 0;
        int low,high;
        for(int i=0;i<n;i++)
        {
            low = i-1;
            high = i+1;
            while(high < n && s[high] == s[i]) high++;
            while(low >=0 && s[low] == s[i]) low--;
            while(high < n && low>=0 && s[low] == s[high])
            {
                low--;
                high++;
            }
            int len = high-low-1;
            if(len > max_len)
            {
                max_len = len;
                start = low + 1;
            }
        }
        return s.substr(start,max_len);
    }
};
```

## Approach 3[Dynamic Programming] :- In these, we use table [2D array] to store each substring's palindrome check. If substring is palindrome, we mark that cell's value with 1 else 0.
- Table is of size n x n where n is the size of string.
- i for row and j for column.
- for example s[i][j] means substring from index i to j. E.g. s = "Harish"     s[3][5] = "ish"
- As we also know that single element is palindrome itself. E.g. cell indices are [i,j] = [0,0], [1,1], [2,2], [3,3] ........
- We also decide the palindrome condtion in substring containing 2 element, if both element are equal mark cell with 1 else 0. E.g. cell indices are [i,j+1] = [0,1], [1,2], [2,3], [3,4], [4,5] .........
- On the basis of previously filled values, we'll fill the remaining cells.

Table Example :-   example string = "abaabc"            
                                                           0   1  2  3  4  5
                                                       0 [ 1, 0, 0, 0, 0, 0]
                                                       1 [ 0, 1, 0, 0, 0, 0]
                                                       2 [ 0, 0, 1, 1, 0, 0]
                                                       3 [ 0, 0, 0, 1, 0, 0]
                                                       4 [ 0, 0, 0, 0, 1, 0]
                                                       5 [ 0, 0, 0, 0, 0, 1]

Now for remaining cells - 
                            if str[i] == str[j] && table[i+1][j-1] == 1
```cpp
// Time Complexity - O(N^2)                 Space Complexity - O(N)
class Solution {
public:
    string longestPalindrome(string s) {
        int n = s.size();
        bool table[n][n];
        memset(table,0,sizeof(table));
        int max_len = 1;
        for(int i=0;i<n;i++) table[i][i] = true;
        
        int start = 0;
        for(int i=0;i<n-1;i++)
        {
            if(s[i] == s[i+1])
            {
                table[i][i+1] = true;
                start = i;
                max_len = 2;
            }
        }
        for(int k=3;k<=n;k++)
        {
            for(int i=0;i<n-k+1;i++)
            {
                int j = i+k-1;
                if(table[i+1][j-1] && s[i] == s[j])
                {
                    table[i][j] = true;
                    if(k > max_len){
                        start = i;
                        max_len = k;
                    }
                }
            }
        }
        return s.substr(start,start+max_len-1);
    }
};
```

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
// Time Complexity - O(N*2)           Space Complexity - O(N)

```

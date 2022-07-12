[Problem Statement](https://leetcode.com/problems/longest-palindrome/submissions/)

## Approach :- Simple approach is based on the occurences of character in string. 
- If character count is even, then its each occurences is utilized in forming the palindrome.
- If character count is odd, then its occurences -1 can be utilized.

```cpp
// Time Complexity - O(N)            Space Complexity - O(1)
class Solution {
public:
    int longestPalindrome(string s) {
        int occurences[128] = {0};
        int len = 0;
        for(char letter : s) occurences[(int)letter]++;
        for(int occu : occurences)
        {
            if(occu%2==0)
                len+=occu;
            else len+=(occu-1);
        }
        if(len < s.size()) len++;
        return len;
    }
};
```

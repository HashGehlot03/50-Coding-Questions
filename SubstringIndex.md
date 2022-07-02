[Problem Statement](https://leetcode.com/problems/implement-strstr/)

## Approach 1[Brute Force] :- In this approach, we simply iterate the haystack using for loop and use inner loop for iterating needle and check if i and j's position value are equal or not.


```cpp
// Time Complexity - O(N^2)             Space Complexity - O(1)
class Solution {
public:
    int strStr(string haystack, string needle) {
        if(haystack.size() == 0 || needle.size() == 0) return -1;
        for(int i=0;i<(haystack.size() - needle.size() + 1);i++)
        {
            int j;
            for(j=0;j<needle.size();j++)
            {
                if(haystack[i+j]!=needle[j]) break;
            }
            if(j == needle.size()) return i;
        }
        return -1;
    }
};
```

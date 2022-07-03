[Problem Statement](https://leetcode.com/problems/implement-strstr/)

[Use it for more approaches](https://alkeshghorpade.me/post/leetcode-implement-strstr)

## Approach 1[Brute Force] :- In this approach, we simply iterate the haystack using for loop and use inner loop for iterating needle and check if i and j's position value are equal or not.


```cpp
// Time Complexity - O(M*N)  where M and N are size of needle and haystack             Space Complexity - O(1)
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

## Approach 2 :- [Knuth-Morris-Pratt algorithm](https://www.youtube.com/watch?v=V5-7GzOfADQ)

```cpp
// Time Complexity - O(M + N) where M and N are size of haystack and needle     Space Complexity - O(1)
class Solution {
public:
    int strStr(string haystack, string needle) {
        if(needle.size() == 0){
            return 0;
        }

        if(haystack.size() < needle.size()){
            return -1;
        }

        int i = 0, j = 0;
        int index;
        while(i < haystack.size()){
            if(haystack[i] == needle[j]){
                index = i;
                while(haystack[i] == needle[j] && j < needle.size()){
                    i++;
                    j++;
                }
                if(j == needle.size()){
                    return index;
                } else {
                    j = 0;
                    i = index + 1;
                }
            } else {
                i++;
            }
        }

        return -1;
    }
};
```

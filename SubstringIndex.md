[Problem Statement](https://leetcode.com/problems/implement-strstr/)


## Approach 1[Brute Force] :- In this approach, we simply iterate the haystack using for loop and use inner loop for iterating needle and check if i and j's position value are equal or not.


```cpp
// Time Complexity - O(M*N)  where M and N are size of needle and haystack             Space Complexity - O(1)
class Solution {
public:
    int* getLpsArr(string str){
      int* lpsArr = (int*) calloc(str.length(), sizeof(int));
      int length = 0;
      int i = 1;
      while(i < str.length()){
        if(str[i] == str[length])
          lpsArr[i++] = ++length;
        else if(length > 0)
          length = lpsArr[length-1];
        else
          lpsArr[i++] = 0;
      }
      return lpsArr;
    }
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
      int n = str1.length();
      int m = str2.length();
      if(m > n)
        return -1;
      if(m == n)
        return str2 == str1 ? 0 : -1;
      if(str2 == "")
        return 0;
      int* lpsArr = getLpsArr(str2);
      int j = 0;
      int i = 0;
      while(i < n && j < m){
        if(str1[i] == str2[j]){
          i++;
          j++;
        }else if(j > 0){
          j = lpsArr[j-1];
        }else{
          i++;
        }
      }
      return j < m ? -1 : i-j;
    }
};
```

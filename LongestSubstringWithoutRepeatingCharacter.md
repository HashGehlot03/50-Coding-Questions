[Problem Statement](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

## Approach 1 [Brute Force]:- The simplest approach to solve this problem is to generate all the substrings of the given string and among all substrings having all unique characters, return the maximum length.
- To generate all substrings of a string, loop from the start till the end index of the string. Let us consider, the start index is i and the end index is j. Run a nested loop from i = 0 to N – 1 and j =  i + 1 till N. Hence, the substrings can be generated.
- To check if the substring contains all unique characters, put all the characters in the set one by one. If any of the characters are already present in the set, skip that string, else consider its length and maximize it.

```cpp
// Time Complexity - O(N^3)         Space Complexity - O(min(N,M))  as N is the length of the string and M is the size of the substrings.
class Solution {
public:
    bool checkUniqueness(string& s, int start, int end){
        unordered_set<char> st;
        for(int i=start;i<=end;i++){
            if(st.find(s[i])!=st.end()) return false;
            st.insert(s[i]);
        }
        return true;
    }
    int lengthOfLongestSubstring(string s) {
        int n = s.length();
        int len_of_max = 0;
        for(int i=0;i<n;i++){
            for(int j=i;j<n;j++){
                if(checkUniqueness(s,i,j)) len_of_max = max(len_of_max,j-i+1);
            }
        }
        return len_of_max;
    }
};
```

## Approach 2 [Sliding Window] :- 
- Run a loop from i = 0 till N – 1 and consider a visited array.
- Run a nested loop from j = i + 1 to N – 1 and check whether the current character S[j] has already been visited.
- If true, break from the loop and consider the next window.
- Else, mark the current character as visited and maximize the length as j – i + 1.
- Remove the first character of the previous window and continue.


```cpp
// Time Complexity - O(N^2)              Space Complexity - O(min(N,M))
class Solution {
public:
    int lengthOfLongestSubstring(string s){
        int n = s.size();
        int res = 0;  
        for (int i = 0; i < n; i++) {
            vector<bool> visited(256);  
 
        for (int j = i; j < n; j++) {
            if (visited[s[j]] == true)
                break;
            else {
                res = max(res, j - i + 1);
                visited[s[j]] = true;
                }
        }
         visited[s[i]] = false;
    }
    return res;
        
    }
};
```

## Approach 3 [Optimized Sliding Window] :- 
- Initialise left = 0 and right = 0.
- Initialise a HashSet to store the characters of the current window.
- Slide the index right  toward N and if it is not present in the current HashSet, slide it further.
- Till this point, we have the maximum non repeating substring length.
- If a character is  found, which is present in the current window, remove the character from the current window and slide further.


```cpp
// Time Complexity - O(N)                Space Complexity - O(N)
class Solution {
public:
    int lengthOfLongestSubstring(string s){
        vector<int> chars(128);
 
        int left = 0;
        int right = 0;
 
        int res = 0;
        while (right < s.length()) {
            char r = s[right];
            chars[r]++;
 
            while (chars[r] > 1) {
                char l = s[left];
                chars[l]--;
                left++;
            }
 
            res = max(res, right - left + 1);
 
            right++;
        }
 
        return res;
        
    }
};
```

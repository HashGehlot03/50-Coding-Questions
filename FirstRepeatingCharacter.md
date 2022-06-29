## Approach 1 :- Use two nested loops and iterate each element and its next element. Then check its frequency and if frequency is greater than 1,return the character

```cpp
// Time Complexity - O(N^2)                Space Complexity - O(1)
class Solution {
public:
        int FirstRepeatingCharacter(string s){
            int count;
            for(int i=0;i<s.size()-1;i++){
                count = 1;
                for(int j=i+1;j<s.size();j++){
                    if(s[i] == s[j]){
                        count++;
                        if(count > 1)
                            return i;
                    }
                    
                }
            }
            return -1;
        }
}
```

## Approach 2 :- In this approach, we'll use unordered set and insert the element by iterating the array. If element exist in set, it means element is occuring more than once therefore return the index position.

```cpp
// Time Complexity - O(N)                Space Complexity - O(N)
class Solution{
public:
        int FirstRepeatingCharacter(string s){
            unordered_set<char> st;
            for(int i=0;i<s.size();i++){
                if(st.find(s[i]!=st.end()) return i;
                st.insert(s[i]);
            }
        }
}
```

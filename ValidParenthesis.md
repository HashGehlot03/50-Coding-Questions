[Problem Statement]()

## Approach [Using stack] :- In this approach, we'll iterate the given string and check the following conditions.
- If it is open bracket, push it in stack.
- If it is closed bracket, check the top of the stack , if it is matching open closing bracket pair, pop from stack else return false.
- Finally if stack becomes empty return true else false.


```cpp
// Time Complexity - O(N)            Space Complexity - O(N)
class Solution {
public:
    bool isValid(string s) {
        unordered_map<char,char> bracketsMap = {{'(',')'},{'{','}'},{'[',']'}};
        vector<char> openBrackets{'(','{','['};
        vector<char> stack;
        for(char bracket : s)
        {
            if(find(openBrackets.begin(),openBrackets.end(),bracket)!=openBrackets.end()) stack.push_back(bracket);   
            else if(stack.size() > 0 && bracket == bracketsMap[stack.back()]) stack.pop_back();
            else return false;
        }
        return stack.size() == 0;
        
    }
};
```

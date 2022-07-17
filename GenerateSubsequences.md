## Generate all subsequences of given string

- String containig n characters has 2^n subsequences

## Approach :- Here in this approach, we'll iterate to each character and consider it taking it or not taking it recursively.

```cpp
// Time Complexity - O(N*2^N)           Space Complexity - O(N*2^N)
void getSubsequencesRec(string str, int i, string subsequence, vector<string> &subsequences){
  if(i == str.size()){
    subsequences.push_back(subsequence);
  }else{
    getSubsequencesRec(str, i+1, subsequence+str.at(i), subsequences);
    getSubsequencesRec(str, i+1, subsequence, subsequences);
  }
}

vector<string> getSubsequences(string str){
  vector<string> subsequences;
  getSubsequencesRec(str, 0, "", subsequences);
  return subsequences;
}

```

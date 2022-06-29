
## Approach 1 :- First use two loops (nested for) in which one loop is for iterating elements of array and another loop iterate its next element and checks the sum is equal to target or not.

```cpp
// Time Complexity :- O(N^2)       Space Complexity :- O(1)
class Solution {
public:
   vector<int> twoSum(vector<int>& nums, int target) {
      int n = nums.size();
      for(int i=0;i<n;i++) {
          for(int j=i+1;j<n;j++) {
              if(nums[i] + nums[j] == target) return {i,j};
          }
      }
      return {1,-1};
   }
}
```

## Approach 2 :- Here we use unordered map where we store elements as a key and its indices as value. Now iterate the array and search that key in map which corresponds to sum of arrays current element and map's key and eventually return its indices.

```cpp
// Time complexity :- O(N)          Space Complexity :- O(N)
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target){
        unordered_map<int,int> m;
        for(int i=0;i<n;i++) {
            int x = nums[i];
            int y = target - nums[i];
            if(m.find(y)!=m.end()) return {i,m[y]};
            m[nums[i]} = i;
        }
        return {1,-1}
    }
}
```

## Approach 3 :- [Two pointer approach] First here we create a integer vector of pair in which pair contains value(as first) and its index(as second) and sort the vector.Now we'll iterate the elements of vector from beginning and ending simultaneously and checks for sum. If sum is lesser than target ,increment beginner counter otherwise end counter.

```cpp
// Time complexity :- O(NlogN)        Space Complexity :- O(N)
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        vector<pair<int, int>> v;
        for(int i=0;i<n;i++) v.push_back({nums[i],i});
        sort(v.begin(),v.end());
        int s=0,e = n-1;
        while(s<e)
        {
            int sum = v[s].first + v[e].first;
            if(sum == target) return {v[s].second,v[e].second};
            else if(sum>target) e--;
            else s++;
        }
        return {-1,-1};
    }
        
};
```

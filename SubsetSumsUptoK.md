Problem Statement - Given an array arr of strictly positive integers, and an integer k, create a function that returns the number of subsets of arr that sum up to k.

## Approach 1 [Recursion] :- In this approach, we'll iterate recursively our array and check the sum is equal to k or not and increment the counter according to it.

```cpp
// Time Complexity - O(2^N)           Space Complexity - O(N)
int subsetsThatSumUpToK(vector<int> arr, int k, int i = 0, int sum = 0){
  if(sum == k)
    return 1;
  else if(sum > k || i >= arr.size())
    return 0;
  else
    return subsetsThatSumUpToK(arr, k, i+1, sum + arr[i]) + subsetsThatSumUpToK(arr, k, i+1, sum);
}

```


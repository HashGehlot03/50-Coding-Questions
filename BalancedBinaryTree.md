[Problem Statement](https://leetcode.com/problems/balanced-binary-tree/)

## Approach 1 :- In this approach, we recursively check the height of left and right subtree then check the absolute difference. If absolute difference between left and right subtree is greater than 1 return false else check further for balanced condition recursively

```cpp
// Time Complexity - O(N)           Space Complexity - O(h)
class Solution {
public:
    int height(TreeNode* root){
        if(!root)
            return -1;
        int leftheight = height(root->left);
        int rightheight = height(root->right);
        return max(leftheight,rightheight) + 1;
        }
      
    bool isBalanced(TreeNode* root){
        if(root == NULL) return true;
        int lefth = height(root->left);
        int righth = height(root->right);
        return abs(lefth - righth) <=1 && isBalanced(root->left) && isBalanced(root->right);
    }
};
```
- In approach 1, we are visiting nodes repeatedly , to overcome this error.

## Approach 2 :- In this approach, we check height of left and right subtree and check its difference lesser than 1 or not.
```cpp
// Time Complexity - O(N)              Space Complexity - O(h)
class Solution {
public:
    bool ans;
    int checkBalance(TreeNode* root){
        if(!root)
            return 0;
        if(!ans) // if Answer is already False then return it.
            return 0;
        int leftSubTree = checkBalance(root->left);
        int rightSubTree = checkBalance(root->right);
        if(abs(leftSubTree-rightSubTree) > 1){
            ans = false;
        }
        return 1 + max(leftSubTree, rightSubTree);
    }
    bool isBalanced(TreeNode* root){
        ans = true;
        int temp = checkBalance(root);
        return ans;
    }
};
```

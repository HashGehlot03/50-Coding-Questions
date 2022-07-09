[Problem Statement](https://leetcode.com/problems/validate-binary-search-tree/)

## Approach 1 :- In this approach, we recursively check all the node's value between its closest left or closest right ancestor value.

```cpp
//Time Complexity - O(N)        Space Complexity - O(h) where h is the height of the BST.
class Solution {
public:
    bool checkValidBST(TreeNode* root, long min, long max){
        if(root == NULL) {
            return true;
        }

        if(root->val <= min || root->val >= max) {
            return false;
        }

        return checkValidBST(root->left, min, root->val) && checkValidBST(root->right, root->val, max);
    }
    bool isValidBST(TreeNode* root){
      if(root == NULL)
        return true;
        return checkValidBST(root, LONG_MIN, LONG_MAX);
    }
};
```

## Approach 2 :- There is a property of BST that if we do inorder traversal in BST, we get the sequence in ascending order. So simple check that the values are sorted or not.

```cpp
// Time Complexity - O(N)            Space Complexity - O(h) where h is the height of the BST.
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        TreeNode * prev = NULL;
        return isValidBST(root, prev);
    }
private:
    bool isValidBST(TreeNode * root, TreeNode* & prev){ // !!important to add "&" since the prev will be changed
    // as traversing down the BST  
        if(root == NULL) return true;
        if(!isValidBST(root->left, prev)) return false;
        if(prev != NULL && prev ->val >= root-> val) return false;
        prev = root;
        return isValidBST(root->right, prev);
    }
};
```

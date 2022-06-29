[Problem Statement](https://leetcode.com/problems/binary-tree-inorder-traversal/)

## Approach 1 :- Using recursion

```cpp
class Solution {
public:
    void help(TreeNode* root,vector<int>& ans)
    {
        if(root == NULL) return ;
        help(root->left,ans);
        ans.push_back(root->val);
        help(root->right,ans);
    }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> ans;
        help(root,ans);
        return ans;
    }
};
```

## Approach 2 :- 

[Problem Statement](https://leetcode.com/problems/binary-tree-postorder-traversal/)

## Approach 1 :- Using recursion

```cpp
class Solution {
public:
    void help(TreeNode* root,vector<int>& ans)
    {
        if(root==NULL) return ;
        help(root->left,ans);
        help(root->right,ans);
        ans.push_back(root->val);
    }
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> ans;
        help(root,ans);
        return ans;
    }
};
```

## Approach 2 :- 

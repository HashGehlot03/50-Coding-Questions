[Problem Statement](https://leetcode.com/problems/binary-tree-preorder-traversal)

## Approach 1 :- Using recursion

```cpp
class Solution {
public:
    void help(TreeNode* root,vector<int>& ans)
    {
        if(root==NULL) return ;
        ans.push_back(root->val);
        help(root->left,ans);
        help(root->right,ans);
    }
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> ans;
        help(root,ans);
        return ans;
    }
};
```
## Approach 2 :- 

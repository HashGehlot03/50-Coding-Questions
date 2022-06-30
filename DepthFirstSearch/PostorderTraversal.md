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

## Approach 2 :- Using 2 Stacks (namely st1 and st2)

- 1 Follow the below steps until st1 is empty.
- 2 First push the root node in st1.
- 3 Now pop the top from st1 and push it in st2.
- 4 Now push the left and right (respectively) of current node(st1's top) in st1.
- 5 Now again pop the top from st1 and push it in st2 and push its left and right in st1.
- Note :- When st1 becomes empty, st2 is the resultant postorder traversal of binary tree. Pop the top of s2 until it is empty and we got our result.

```cpp
class Solution {
public:
        vector<int> postorderTraversal(Treenode* root){
                vector<int> postOrder;
                if(root == NULL) return postOrder;
                stack<Treenode*> st1, st2;
                st1.push(root);
                while(!st1.empty()) {
                        root = st1.top();
                        st1.pop();
                        st2.push(root);
                        if(root->left!=NULL) st1.push(root->left);
                        if(root->right!=NULL) st1.push(root->right);
                        while(!st2.empty()) {
                                postOrder.push_back(st2.top()->val);
                                st2.pop();
                        }
                        return postOrder;
                }
        }
}
```

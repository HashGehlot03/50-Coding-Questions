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

## Approach 2 :- Using stack

```cpp
class Solution {
public:
        vector < int > inOrderTrav(node * curr) {
                vector < int > inOrder;
                stack < node * > s;
                while (true) {
                        if (curr != NULL) {
                            s.push(curr);
                            curr = curr -> left;
                        }
                        else {
                            if (s.empty()) break;
                            curr = s.top();
                            inOrder.push_back(curr -> data);
                            s.pop();
                            curr = curr -> right;
                            }
                        }
                        return inOrder;
       }
}
```

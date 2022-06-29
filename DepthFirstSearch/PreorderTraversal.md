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
## Approach 2 :- Using stack

```cpp
class Solution {
public:
        vector < int > preOrderTrav(node * curr) {
                vector < int > preOrder;
                if (curr == NULL) return preOrder;

                stack < node * > s;
                s.push(curr);

                while (!s.empty()) {
                        node * topNode = s.top();
                        preOrder.push_back(topNode -> data);
                        s.pop();
                        if (topNode -> right != NULL) s.push(topNode -> right);
                        if (topNode -> left != NULL) s.push(topNode -> left);
                }
                return preOrder;

        }
}
```

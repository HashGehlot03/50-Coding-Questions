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

- 1 First push the root node in stack.
- 2 Pop the top and push its right then its left if exist. (Here we are pushing right first and left second just because when we pop,we first encounter left child which follows the preorder traversal.)
- 3 Again follow the above steps until the stack is empty.
- 4 Pop the top and push its right then its left if exist.
- 5 Same as 3.
- Note :- At every iteration, element which is popped is printed out or maybe store in vector

```cpp
class Solution {
public:
        vector <int> preOrderTrav(node * root) {
                vector <int> preOrder;
                if (root == NULL) return preOrder;

                stack <node *> s;
                s.push(root);

                while (!s.empty()) {
                        node * topNode = s.top();
                        preOrder.push_back(topNode -> data);   //We can print here also 
                        s.pop();
                        if (topNode -> right != NULL) s.push(topNode -> right);
                        if (topNode -> left != NULL) s.push(topNode -> left);
                }
                return preOrder;

        }
}
```

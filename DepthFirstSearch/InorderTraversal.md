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

- 1 Push the root node to stack.
- 2 Iterate to the left and push the element until root->left != nullptr .
- 3 When we encounter nullptr, pop the top and assign stack's top element right to current node.
- 4 If again it is empty,pop the stack's top and assign its right to current and if not,iterate to left until nullptr.
- Note :- When popping, we can store the element in output array or we can print directly

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

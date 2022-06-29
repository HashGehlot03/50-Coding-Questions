[Problem Statement](https://leetcode.com/problems/invert-binary-tree/]

## Approach :- Using recursion,we'll iterate the left then right subtree recursively and swap the left and right.

```cpp
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if(root!=nullptr)
        {
                            invertTree(root->left);
            invertTree(root->right);
            TreeNode* temp = root->left;
            root->left = root->right;
            root->right = temp;
        }
        return root;
        
    }
};
```

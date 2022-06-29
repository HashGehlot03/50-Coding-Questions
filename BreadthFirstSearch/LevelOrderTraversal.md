[Problem Statement](https://leetcode.com/problems/binary-tree-level-order-traversal/)

## Approach 1 :- Using queue

```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        if(!root) return {};
        vector<vector<int>> result;
        queue<TreeNode*> Q;
        Q.push(root);
        while(!Q.empty())
        {
            int count = Q.size();
            vector<int> level_nodes;
            for(int i=0;i<count;++i)
            {
                TreeNode * node = Q.front();
                Q.pop();
                if(node->left) Q.push(node->left);
                if(node->right) Q.push(node->right);
                level_nodes.push_back(node->val);
            }
            result.push_back(level_nodes);
        }
        return result;
    }
};
```

[Problem Statement](https://leetcode.com/problems/binary-tree-level-order-traversal/)

## Approach 1 :- Using queue
- 1 First push the root node in queue.
- 2 Maintain the variable for queue size.
- 3 Pop the front and push its left and right if exist.
- 4 Follow the 4th above steps(2 & 3) until the queue is empty.
- Note :- When popping the element, push it in array and then push that array in 2D array (To store level order traversal)

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

## 剑指Offer[4]——重建二叉树
### 问题描述
输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。
假设输入的前序遍历和中序遍历的结果中都不含重复的数字。
例如输入前序遍历序列`{1,2,4,7,3,5,6,8}`和中序遍历序列`{4,7,2,1,5,3,8,6}`，则重建二叉树并返回。

### 考点
- 树的遍历

### 思路
前序为中、左、右，中序为左、中、右。

首先，前序序列`pre`中的首位`n`必为根节点，在中序序列`vin`中找到相应的数字`n`，则`vin`中`n`左侧的必为左子树结点，右侧为右子树结点。

相应地，根据`vin`中得到的左右子树大小可以分割`pre`为左子树和右子树。

然后递归求解，直到startPre>=endPre||startIn>=endIn说明子树整理完。
`construct`方法每次返回左子树和右子树的根节点。

需要注意的是，左子树大小的计算，应为`i - vinStart + 1`。
代码中的Start和End均为左闭右开区间。

### 代码
~~~cpp
/**
 * Definition for binary tree
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
 public:
  TreeNode* reConstructBinaryTree(vector<int> pre, vector<int> vin) {
    return construct(pre, 0, pre.size(), vin, 0, vin.size());
  }

  TreeNode* construct(vector<int> pre, int preStart, int preEnd, vector<int> vin, int vinStart, int vinEnd) {
    if (preStart >= preEnd || vinStart >= vinEnd) return NULL;
    TreeNode* root = new TreeNode(pre[preStart]);
    for (int i = vinStart; i < vinEnd; i++) {   
      if (vin[i] == pre[preStart]) {  /* 在vin中找到根节点 */
        root->left = construct(pre, preStart + 1, preStart + 1 + i - vinStart, vin, vinStart, i);
        root->right = construct(pre, preStart + 1 + i - vinStart, preEnd, vin, i + 1, vinEnd);
        break;
      }
    }
    return root;
  }
};
~~~

# 2025.12.28
坏了，今天又回到之前那个啥事没干的状态了，下午四点才睡的午觉，得改。

## 力扣每日一题:
  226.翻转二叉树
  [https://leetcode.cn/problems/invert-binary-tree?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 特别简单的递归，怎么最近刷的都是这些基础题。
  ```python
  class Solution(object):
    def invertTree(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: Optional[TreeNode]
        """
        if root is None:
            return 
        
        self.invertTree(root.left)
        self.invertTree(root.right)
        root.left, root.right = root.right, root.left
        return root

## 每日碎碎念
* 还是抢不到票
* 这两天太颓废，太焦虑了，还是太闲了，得改。

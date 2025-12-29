# 2025.12.27
玩了一下午的青椒模拟器，有点上头。

## 力扣每日一题:
  104.二叉树的最大深度
  [https://leetcode.cn/problems/maximum-depth-of-binary-tree?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 特别简单的递归，三行解决，不过不是尾递归，在性能上还能优化，等我二刷再说吧。
  ```python
  class Solution(object):
    def maxDepth(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        if root is None:
            return 0
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1

## 每日碎碎念
* 还是抢不到票
* 青椒模拟器好玩捏，不过被研究生牛马生活吓哭了，论文写出来还不够，还得等投，投了又不一定中，难难难。

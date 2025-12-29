# 2025.12.29
今天看了下自控的PPT，发现其实不太难？也有可能是我已经过了一遍can博的综述课了。

## 力扣每日一题:
  226.对称二叉树
  [https://leetcode.cn/problems/symmetric-tree?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 有点上难度了，但是我发现其实这种test机制本身也是一个限制，当你函数本身的输入和你的想法不一样时，就需要引入新函数了。
  ```python
  class Solution(object):
    def isSameTree(self, p, q):
        if p is None or q is None:
            return p is q
        return p.val == q.val and self.isSameTree(p.left, q.right) and self.isSameTree(p.right, q.left)


    def isSymmetric(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        return self.isSameTree(root.left, root.right)

## 每日碎碎念
* 还是抢不到票
* 今天看了会书，不赖。

# 2025.12.26
看了篇ORPO的blog。

## 力扣每日一题:
  94.二叉树的中序遍历
  [https://leetcode.cn/problems/binary-tree-inorder-traversal?envType=study-plan-v2&envId=top-100-liked]

### 思路：
麻了，编码能力太差了，还在思考要不要print，还是靠内置函数才解决的。
- 普通实现：就简单的前序遍历递归
  ```python
  class Solution(object):
    def inorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        def dfs(node):
            if node is None:
                return None
            dfs(node.left)
            ans.append(node.val)
            dfs(node.right)

        ans = []
        dfs(root)
        return ans

- 线索二叉树（Morris遍历）：对于一个节点，它的前置节点等于左节点的右节点到空，产生一个连接，这样就可以直接从一个右节点为空的点直接跳回之前的节点，不需要递归栈去储存信息，在跳过后，顺手删除即可（不删除也行其实，只要保证前置节点只经过一遍就行），然后返回当前节点所在的值，这样在保证不重复经过前置节点的情况下，就会以正常顺序返回前序遍历的结果。
  ```python
  class Solution(object):
    def inorderTraversal(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        ans = []

        while root:
            if root.left:
                pre = root.left
                while pre.right and pre.right is not root:
                    pre = pre.right

                if pre.right is None:
                    pre.right = root
                    root = root.left
                    continue
                
                pre.right = None
        
            ans.append(root.val)
            root = root.right

        return ans
## 每日碎碎念
* 还是抢不到票
* 今天在BOSS直聘上聊了一下，发现要考研的话确实不易拿出太多精力去其他地方，毕竟实习不能说到时间拍拍屁股就走人的，起码得把对应任务做完，不然到时候恶心所有人。
* 被牢美斩杀线机制吓哭了，挺绝望的社会。

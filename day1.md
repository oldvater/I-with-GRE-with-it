# 2025.12.20
26开始考研的第一天，也是27开始备考的第一天

## 力扣每日一题:
  19. 删除链表的倒数第 N 个结点
  [https://leetcode.cn/problems/remove-nth-node-from-end-of-list?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 现将链表反转，把问题简化为删除链表的第N个节点，在将执行删除操作后的链表反转回来，就得到了删除倒数第N个节点。
  ```python
  class Solution(object):
      def removeNthFromEnd(self, head, n):
          """
          :type head: Optional[ListNode]
          :type n: int
          :rtype: Optional[ListNode]
          """
          pre, cur = None, head
          while cur:
              temp = cur.next
              cur.next = pre
              pre, cur = cur, temp
          l = ListNode()
          m = l
          l.next = pre
          while n - 1:
              l = l.next
              n -= 1
          l.next = l.next.next
          aft = None
          pre = m.next
          while pre:
              temp = pre.next
              pre.next = aft
              aft, pre = pre, temp
          return aft
- 建立一个滑动窗口，窗口的左端在最开始建立的哨兵节点，窗口右端在第n + 1个节点，这样，当窗口右端到达最后一个节点时，窗口左端就到达了倒数第n + 1个节点，也就是左端的next就指向了倒数第n个节点，删除即可。
  ```python
  class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: Optional[ListNode]
        :type n: int
        :rtype: Optional[ListNode]
        """
        left = right = dummy = ListNode()
        dummy.next = head
        for _ in range(n):
            right = right.next
        while right.next:
            left = left.next
            right = right.next
        left.next = left.next.next
        return dummy.next                          //防止删除head节点，不直接访问head，而是访问哨兵阶段的next
## 每日碎碎念
今天是26考研的第一天，如果不降转的话我估计也是今天考，但我降了一级，所以明年的现在才是我的战场。
老是说要考研，得考研，但真正要备考了还是有点慌的，希望这一年里加油吧。
今天主要还是把目前的课给复习，过了，专业课和数学的事情等下学期再说吧。


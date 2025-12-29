# 2025.12.21
26考研结束，27考研正式拉开帷幕。

## 力扣每日一题:
  24. 两两交换链表中的节点
  [https://leetcode.cn/problems/swap-nodes-in-pairs?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 迭代：先确定要交换的两个点first， second和前点的前一个节点pre，交换两个节点的next，然后pre连接到second上，完成修改后把pre赋值为first
  ```python
  class Solution(object):
    def swapPairs(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        pre = dummy = ListNode(next = head)
        while pre.next and pre.next.next:
            first = pre.next
            second = pre.next.next

            pre.next = second
            first.next = second.next
            second.next = first

            pre = first

        return dummy.next
- 递归：先做判断：如果包含头结点在内的剩余节点少于两个，则直接返回头结点，否则将头结点head看作node1， head.next看作node2，node2.next看作node3，现在要交换的就是node1和node2，将node2.next改为node1, 将node3作为新头结点，带入函数接到node1.next。
  ```python
  class Solution(object):
    def swapPairs(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if head is None or head.next is None:
            return head
        
        node1 = head
        node2 = head.next
        node3 = node2.next

        node1.next = self.swapPairs(node3)
        node2.next = node1

        return node2
25.K个一组翻转链表
  [https://leetcode.cn/problems/reverse-nodes-in-k-group?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 递归（只会这个）：依然先做判断：如果包含头结点在内的剩余节点少于K个，则直接返回头结点，否则将头结点head看作node1， 第K个节点看作node2，node2.next看作node3，现在要翻转的就是node1和node2之间的所有节点，直接写翻转链表节点函数就行，没什么好说的，翻转后，这时候头节点应该是node2处，尾巴是node1，将node3作为新头结点，带入函数接到node1.next。
  ```python
  class Solution(object):
    def reverseKGroup(self, head, k):
        """
        :type head: Optional[ListNode]
        :type k: int
        :rtype: Optional[ListNode]
        """
        dummy = head
        if head is None or head.next is None:
            return dummy
        for i in range(k - 1):
            if head is None or head.next is None:
                return dummy
            head = head.next
        
        node1 = dummy
        node2 = head
        node3 = node2.next
        cur = node1.next
        while node1 != node2:
            temp = cur.next
            cur.next = node1
            node1 , cur = cur, temp

        dummy.next = self.reverseKGroup(node3, k)

        return node2

## 每日碎碎念
今天26考研结束了，有一说一，今年数学偏简单，408难，让我有点没信心了，我真的能考上吗，不过还是得试试，考上了享受荣华富贵，考不上就找个厂月入7000，努力一年试试吧。
今天本来只打算写一题的，但是发现24题的思路就是25的思路，本着“来都来了，趁热打铁”的想法，还是写了两道题。
有一说一，这个趋势有的有既视感是怎么回事？数学简单，英语不难，政治中等，但副科特别难，让我想起了21年湖南高考。希望不要重现22年高考的噩梦。

# 2025.12.22
备考第一天这一块

## 力扣每日一题:
  138.随机链表的复制
  [https://leetcode.cn/problems/copy-list-with-random-pointer?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 哈希表法：首先把val和next复制下来，组成一个普通复制链表，然后使用字典dict1储存与原节点对应的复制节点，这样我们就可以从原链表直接跳到复制链表的对应节点。然后遍历原链表和新链表，由于原链表的random依旧指向原链表，因此得靠dict1把random节点转化到新链表的对应节点，实现random的复制。之后返回新链表的头节点即可。
  ```python
  class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        pre = dummy = Node(0)
        node1 = head
        dict1 = {}
        while head:
            cur = Node(head.val)
            dict1[head] = cur
            pre.next = cur
            pre, head = cur, head.next

        head = dummy.next

        while node1:
            if node1.random:
                head.random = dict1[node1.random]
            head = head.next
            node1 = node1.next

        return dummy.next
- 切割链表法：把新链表直接放到原链表对应节点的后面，比如从1->2->3变成1->1'->2->2'->3->3'，这样就可以很轻松地复制random值。然后将该链表变成1->2->3和1'->2'->3'即可。注意要回复原链表。
  ```python
  class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        if head is None:
            return None

        cur = head
        while cur:
            cur.next = Node(cur.val, cur.next)
            cur = cur.next.next

        cur = head

        while cur:
            if cur.random:
                cur.next.random = cur.random.next
            cur = cur.next.next

        cur = head
        new_head = head.next
        while cur.next.next:           //分割链表。copy表示新链表，cur表示原链表，先赋值copy，
            copy = cur.next            //然后修改cur.next，然后再修改copy.next
            cur.next = copy.next
            copy.next = copy.next.next
            cur = cur.next

        cur.next = None

        return new_head
## 每日碎碎念
今天顺位继承了the刘的座位，然后学了一下午，感觉有点紧张，又没有那么紧张，主要是感觉自己从看别人考研的那个变成了考研的那个
，再也不能玩考研笑话了（悲）。然后今天还去BOSS直聘看了看实习，乱投简历这一块，看看结果怎么样吧。

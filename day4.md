# 2025.12.23
去boss直聘上乱投实习，发现实习岗位要求都太高了，在学有余力的情况下尽量往后学吧。

## 力扣每日一题:
  148.排序链表
  [https://leetcode.cn/problems/sort-list?envType=study-plan-v2&envId=top-100-liked]

### 思路：
本来最开始是选择了冒泡排序来实现排序，时间复杂度为O(n^2),结果冒出来一个超大数据集把我肘飞了，没办法，只能采取归并排序。
- 递归：就是把一个链表分成两份，然后直到最小有序链表单元（一个）时，两两排序，然后合并，这样最小有序链表单元的规模就变成了两个，依次类推，最后经过合并后返回的就是原大小的有序链表了。
  ```python
  class Solution(object):
    def middle(self, head):
        slow = fast = head
        while fast and fast.next:
            pre = slow
            slow = slow.next
            fast = fast.next.next
        pre.next = None
        return slow

    def merge(self, l1, l2):
        dummy = head = ListNode()
        while l1 and l2:
            if l1.val < l2.val:
                head.next = l1
                l1 = l1.next
            else:
                head.next = l2
                l2 = l2.next
            head = head.next
        head.next = l1 or l2

        return dummy.next 
    
    def sortList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        if head is None or head.next is None:
            return head

        mid = self.middle(head)
        
        left = self.sortList(head)
        right = self.sortList(mid)

        return self.merge(left, right)
- 迭代法：递归法是从上到下（链表大小从大到小），迭代法就是从小到大，一开始就把有序链表规模k定为1，然后每2段相应规模链表就进行一次排序，然后将k*=2，重复进行排序直到k>n。
  ```python
  class Solution(object):
    def leng(self, head):
        n = 0
        while head:
            n += 1
            head = head.next
        return n

    def split(self, head, n):
        cur = head
        for _ in range(n - 1):
            if cur is None:
                break
            cur = cur.next

        if cur is None or cur.next is None:
            return None

        next_head = cur.next
        cur.next = None

        return next_head

    def merge(self, l1, l2):
        dummy = head = ListNode()
        while l1 and l2:
            if l1.val < l2.val:
                head.next = l1
                l1 = l1.next
            else:
                head.next = l2
                l2 = l2.next
            head = head.next
        head.next = l1 or l2

        while head.next:
            head = head.next

        return dummy.next, head
    
    def sortList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        n = self.leng(head)
        dummy = ListNode(next=head)
        step = 1
        while step < n:
            new_list_tail = dummy
            cur = dummy.next

            while cur:
                head1 = cur
                head2 = self.split(head1, step)
                cur = self.split(head2, step)
                head, tail = self.merge(head1, head2)
                new_list_tail.next = head
                new_list_tail = tail
            
            step *= 2

        return dummy.next
## 每日碎碎念
* 实习好难找啊啊啊，要求都太高了，主要还是我简历太薄了，那我问你，我是不是要先找实习才能有实习经历，我是不是得有实习经历才能找你的实习，那我问你。
总结：要么发论文，要么打竞赛，没办法。
* 今天学了计租的cache的几种映射，有一说一，这些在我学单片机的时候就接触过一遍了，还算能跟上。
* transformer好难理解啊，刚看了一遍李沐的transformer论文解读，还是有一些不太理解的地方，明天看看3b1b的视频理解一下。

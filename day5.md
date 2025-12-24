# 2025.12.24
平安夜，看了会Transformer，大概能理解模型讲啥了，然后开始复习自控。

## 力扣每日一题:
  23.合并K个升序链表
  [https://leetcode.cn/problems/merge-k-sorted-lists?envType=study-plan-v2&envId=top-100-liked]

### 思路：
这题最开始看到我就想把归并算法运用到链表列表中，每一个链表都可以对应列表中的元素，只需要保证单一元素具有有序性，就可以进行合并排序，用之前写的merge进行合并即可。不过我还看到了堆的做法？待我写完堆后二刷回来再看看。
- 递归：和数组的归并排序逻辑类似，我们手里已经有了能保证每个元素都有序的数组，元素之间的有序合并逻辑，那就可以使用归并算法（暴论）。递归就是从上到下
  ```python
  class Solution(object):
    def merge(self, l1, l2):
        head = dummy = ListNode()
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
    def mergeKLists(self, lists):
        """
        :type lists: List[Optional[ListNode]]
        :rtype: Optional[ListNode]
        """
        n = len(lists)
        if n == 0:
            return None
        if n == 1:
            return lists[0]
        left = self.mergeKLists(lists[0:n // 2])
        right = self.mergeKLists(lists[n // 2:])
        return self.merge(left, right)
- 迭代法：逻辑同数组的归并算法。，递归法是从上到下（链表大小从大到小），迭代法就是从小到大，一开始就把排序组规模step定为1，然后每2段相应规模元素就进行一次合并，然后将step*=2，重复进行排序直到k>n。
  ```python
  class Solution(object):
    def merge(self, l1, l2):
        head = dummy = ListNode()
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
    def mergeKLists(self, lists):
        """
        :type lists: List[Optional[ListNode]]
        :rtype: Optional[ListNode]
        """
        n = len(lists)
        if n == 0:
            return None
        step = 1
        while step < n:
            i = 0
            while i < n - step:
                lists[i] = self.merge(lists[i], lists[i + step])
                i += 2*step
            step *= 2

        return lists[0]
## 每日碎碎念
* 有点惆怅，感觉408好多，主要还是没那个氛围了，周围的熟人基本上都已经考完研了，有种物是人非的错觉？
* 有一说一，我对自控这门课开始迷茫了，学吧，不是专业课学了太亏；不学吧，下学期一堆课都依赖这个，不学下学期直接看不懂，算了，先复习着吧。
* transformer大概能理解主要模块是干什么的了。encoder的自注意力就是根据输入快速形成全局词性（比如水课和水库里的水大抵是不一样的，就得靠这个自注意力进行区分），然后生成一个可供查询的字典K：V，decoder的掩码注意力就是根据输出生成对应词性
（知道自己在什么主题，需要什么），产生查询矩阵Q，让查询矩阵Q与K进行注意力检测（实际上就是利用V的线性组合更新最终输出），然后经过一个全分类器，产生输出。
### 上面就是我对transformer的理解，希望我以后回来看这个的时候不要笑出声，不过还需要看一下实现代码，我的编码能力还是不够强。

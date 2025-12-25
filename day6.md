# 2025.12.25
Marry Cristmas!今天看了会SFT的blog，看了会lora

## 力扣每日一题:
  146.LRU缓存
  [https://leetcode.cn/problems/lru-cache?envType=study-plan-v2&envId=top-100-liked]

### 思路：
这题我会！我昨天刚学过LRU的机制，我不乱杀？什么叫计数器加加是错误的？什么叫必须要O（1）复杂度？计组里根本不是这么写的，你应该每个cache行都设置一个计数器，然后操作到你的时候清0，否则加一，然后删除的时候挑最高的删，什么叫超时？什么叫双向链表？不对，计组里不是这么写的！
- 计组实现：超时了，为什么按原理来通过不了啊，优化这么卷了吗？
  ```python
  class LRUCache(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.capacity = capacity
        self.s = {}
        self.count = {}
        

    def get(self, key):
        """
        :type key: int
        :rtype: int
        """
        s = self.s
        cnt = self.count
        if key not in s:
            return -1
        cnt[key] = -1
        for i in s:
            cnt[i] += 1
        return s[key]
        

    def put(self, key, value):
        """
        :type key: int
        :type value: int
        :rtype: None
        """
        s = self.s
        n = self.capacity
        cnt = self.count
        if key not in s:
            if len(s) == n:
                max_key = max(cnt, key = cnt.get)
                s.pop(max_key)
                cnt.pop(max_key)    
        s[key] = value 
        cnt[key] = -1
        for i in s:
            cnt[i] += 1

- 双头链表：优化版，实现了一个双向链表，操作一个key的时候，把它移到最前面，需要删除的时候删除最后的元素就行。
  ```python
  class Node():
    __slots__ = 'prev', 'next', 'key', 'value'

  class LRUCache:
      def __init__(self, capacity):
          self.capacity = capacity
          self.dummy = Node()
          self.dummy.next = self.dummy
          self.dummy.prev = self.dummy
          self.s = {}

      def getnode(self, key):
          if key not in self.s:
              return None

          node = self.s[key]
          self.remove(node)
          self.tohead(node) 
          return node

      def get(self, key):
          if key not in self.s:
              return -1
          node = self.getnode(key)
          return node.value

      def put(self, key, value):
          if key not in self.s:
              node = Node()
              node.key = key
              node.value = value
              self.tohead(node)
              self.s[key] = node
          node = self.getnode(key)
          node.value = value
          if len(self.s) > self.capacity:
              del_node = self.dummy.prev
              self.remove(del_node)
              del self.s[del_node.key]

      def remove(self, node):
          node.prev.next = node.next
          node.next.prev = node.prev

      def tohead(self, node):
          node.next = self.dummy.next
          node.prev = self.dummy
          node.prev.next = node
          node.next.prev = node
## 每日碎碎念
* 不是，为啥买不到回家的票啊（悲），为什么开抢秒进递补啊，为什么不放票啊啊啊啊啊啊！！！！
* 看了会SFT的实现blog，寒假的时候跟着调一下？
* 佳焙西点好吃捏。
* 为什么要有手写实验报告这个东西啊，有毒啊

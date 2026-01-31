# 2026.1.31
昨天路过娄底，今天已达长沙，玩。

## 力扣每日一题:
  155.最小栈
  [https://leetcode.cn/problems/min-stack?envType=study-plan-v2&envId=top-100-liked]

### 思路：
- 可以用两个数组来构建，一个数组用来存栈的数组，另一个用作存储历代最小值的辅助数组，当新压入的值小于之前存的最小值时，
  将新值压入，这样删除最小值时，下一个就是之前的最小值，也就是次小值，就可以读取了。
  ```python
  class MinStack(object):

    def __init__(self):
        self.stack1 = []
        self.stack2 = [float('inf')]
        

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        self.stack1.append(val)
        if val <= self.stack2[-1]:
            self.stack2.append(val)
        

    def pop(self):
        """
        :rtype: None
        """
        x = self.stack1.pop()
        if x == self.stack2[-1]:
            self.stack2.pop()
        return x
        

    def top(self):
        """
        :rtype: int
        """
        return self.stack1[-1]
        

    def getMin(self):
        """
        :rtype: int
        """
        return self.stack2[-1]


## 每日碎碎念
* 已达长沙，玩。

# 2026.3.4
假期过得真快啊，两个月感觉一下子就过去了，该回学校了。



## 进度看板

| 优先级 | 单元名称 | 总预算 (Hot100题数) | 当前进度 | 剩余天数 | 状态 | 备注 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 数组/哈希 | 8  | 0/8 | 8 | ⏳ 待开始 | 完成难度分 ≤1700 的题目，下同 |
| 2 | 滑动窗口与双指针 | 6  | 1/6 | 6 | 开始 | |
| 3 | 二分查找 | 6  | 0/6 | 6 | ⏳ 待开始 | |
| 4 | 数据结构（栈，堆） | 8  | 0/8 | 8 | ⏳ 待开始 | |
| 5 | 链表 | 14  | 0/14 | 14 | ⏳ 待开始 | 重点复习反转/环 |
| 6 | 二叉树 | 15 | 0/15 | 15 | ⏳ 待开始 | 第一轮只做递归 |
| 7 | 图 | 8 | 0/8 | 8 | ⏳ 待开始 | |
| 8 | 回溯 | 8 | 0/8 | 8 | ⏳ 待开始 | 一口气刷完 |
| 9 | 贪心 | 4 | 0/4 | 4 | ⏳ 待开始 | 一口气刷完 |
| 10 | 动态规划 | 15 | 0/15 | 15 | ⏳ 待开始 | 前六章，难度分 ≤2000 的题目 |


### 当前周期 (Week 1)
- **目标单元**：[滑动窗口与双指针]
- **周期剩余**：5 天 

---
*注：超过7天若未完成，将状态改为“🔄 挂起”，填入剩余天数，然后开启下一行单元。*
## 力扣每日一题:
- 1456.定音子串中元音的最大数目
  [https://leetcode.cn/problems/maximum-number-of-vowels-in-a-substring-of-given-length]

## 思路：
- 额，由于没有在灵神的题单里找到专门的数组/哈希表单元，因此先从双指针与滑动窗口开始。
  这题是典型的定长滑动窗口，只需要维护一个长度为k的窗口，对于下标是i的右边界，左边界为i-k+1,
  当左边界小于零，即滑动窗口的有效长度不足k时，继续往右扩张，当有效长度为k，也就是左边界为0时，
  循环执行：加入右边界->更新参数->删除左边界的操作即可。
  对于这题，就是维护最大的元音字母个数，因此引入一个中间变量vowel，当元音加入，vowel加一，当元音删除，vowel减一，
  期间不断维护vowel的最大值ans即可。
```python
  class Solution(object):
    def maxVowels(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        n = len(s)
        ans = vowel = 0
        for i, c in enumerate(s):
            if c in "aeiou":
                vowel += 1
            
            left = i - k + 1
            if left < 0:
                continue
            ans = max(ans, vowel)
            if ans == k:
                return k

            if s[left] in "aeiou":
                vowel -= 1
        
        return ans
```
- 3679.使库存平衡的最少丢弃次数
  [https://leetcode.cn/problems/minimum-discards-to-balance-inventory]

## 思路：
- 这题主要得考虑到被丢弃的数在滑动窗口中是一种被“除名”的存在，因此，滑动窗口弹出的时候只能弹出未被丢弃的值。
  本题设立一个哈希表（我用的字典）来记录物品出现的频率，当频率大于m时，就需要丢弃该数，由于是一个一个加入的窗口，
  因此只需要设置一个加入后大于m，对应的count减一就行，同时要注意丢弃过的数在弹出的时候不能影响正常数的记录，
  因此修改被丢弃的东西的值为0，这样弹出时减的也只会是0的频率，而加入发生在修改之前，不会受到影响。
```python
  class Solution(object):
    def minArrivalsToDiscard(self, arrivals, w, m):
        """
        :type arrivals: List[int]
        :type w: int
        :type m: int
        :rtype: int
        """
        count = {}
        ans = 0
        count[0] = 0
        for i, x in enumerate(arrivals):
            if x not in count:
                count[x] = 1
            else:
                count[x] += 1
            
            left = i - w + 1
            if count[x] > m:
                count[x] -= 1
                ans += 1
                arrivals[i] = 0

            if left < 0:
                continue
            
            count[arrivals[left]]  -= 1
        
        return ans
```

## 每日碎碎念
* 明天就要去学校了，ε=(´ο｀*)))唉。
* 我草，好勾八焦虑啊，今年考研分数太高了，看着那些400扎堆的分数好无力啊。
* 先刷题吧，争取7月之前结束一轮。
* 明天落地哈尔滨，玩一天再去学校，嘿嘿。
* 明天，奶奶去医院检查，希望这次检查能缓解一下咳嗽吧。

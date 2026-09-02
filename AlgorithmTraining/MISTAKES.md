# Mistake Patterns

## 看到连续子数组求和就直接使用滑动窗口

Status: Active
First Seen: 2026-08-20
Last Seen: 2026-08-20

### Occurrences

- Session 001 — LeetCode 560

### Correction

先判断窗口扩张或收缩时目标量是否具有足够的单调性；含负数的等和计数问题优先考虑前缀和加哈希。

## 未验证值域覆盖与出现次数条件就使用总和差

Status: Active
First Seen: 2026-08-22
Last Seen: 2026-08-22

### Occurrences

- Session 003 — 综合辨析 Q3

### Correction

使用总和差前先验证数组是否恰由 `1..n` 各一次再加一个额外副本组成；若只保证值域和唯一重复值，应利用“数组值可作为下一索引、重复值造成路径汇合”的结构推理。

## 复杂度结论未逐层对应实际操作成本

Status: Active
First Seen: 2026-08-21
Last Seen: 2026-09-02

### Occurrences

- Session 002 — LeetCode 875
- Session 004 — LeetCode 1475
- Session 004 — LeetCode 128
- Session 007 — LeetCode 128
- Session 009 — LeetCode 875
- Session 013 — LeetCode 128

### Correction

给出复杂度前逐层列出循环、判定函数和成员查询的实际成本，并严格区分“常数级 O(1)”与“线性级 O(n)”；还要确认外层遍历域是否去重、每次内层工作是否有唯一触发者。`set`/`dict` 成员查询平均 O(1)，`tuple`/`list` 成员查询为 O(n)，嵌套或重复调用的成本需要相乘而不是相加，例如 O(n) 判定执行 O(log m) 次应为 O(n log m)。

## 未区分目标关系就把含负数子数组统一归为前缀和加哈希

Status: Active
First Seen: 2026-08-24
Last Seen: 2026-08-25

### Occurrences

- Session 005 — LeetCode 209
- Session 006 — LeetCode 930

### Correction

先区分目标是“和恰好等于某值”的查询或计数，还是“和至少/至多某值并求最短或最长”的不等式最优化；哈希适合精确差值查询和计数，不能单独覆盖所有连续区间问题。

## 未先固定前缀定义与区间边界就写求和等式

Status: Resolved
First Seen: 2026-08-25
Last Seen: 2026-08-27

### Occurrences

- Session 006 — LeetCode 724
- Session 008 — LeetCode 2574

### Correction

写求和等式前先明确前缀和或滚动累计量是否包含当前位置，以及题目左右区间是否包含中心元素；若累计量 k 表示 i 左侧和，则当前右侧和必须写成 `total - k - nums[i]`，计算后才能把 `nums[i]` 加入 k。

## 只证明二分区间会收敛，未证明收敛点满足答案定义

Status: Active
First Seen: 2026-08-28
Last Seen: 2026-08-28

### Occurrences

- Session 009 — LeetCode 35

### Correction

写边界二分前先定义被排除区间各自满足的性质；例如维护 `[0, left)` 全部小于目标、`[right, n)` 全部大于等于目标，循环结束时再由 `left = right` 推出该点满足答案定义。边界移动只能证明终止，不能单独证明返回值正确。

## 链表改指针前未主动固定后继可达性与终止不变量

Status: Active
First Seen: 2026-08-25
Last Seen: 2026-08-30

### Occurrences

- Session 006 — LeetCode 143
- Session 011 — LeetCode 143

### Correction

每次覆盖 `next` 前先命名并保存仍需访问的后继，并明确结果入口、已处理部分和未处理部分；多段链表合并还要先比较两段长度，写出循环终止时为什么不会丢失剩余节点，不能只用目标形状代替指针安全证明。

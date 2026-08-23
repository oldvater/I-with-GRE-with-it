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
Last Seen: 2026-08-23

### Occurrences

- Session 002 — LeetCode 875
- Session 004 — LeetCode 1475
- Session 004 — LeetCode 128

### Correction

给出复杂度前逐层列出循环、判定函数和成员查询的实际成本；`set`/`dict` 成员查询平均 O(1)，`tuple`/`list` 成员查询为 O(n)，嵌套或重复调用的成本需要相乘而不是相加。


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


# Mistake Patterns

## 看到连续子数组求和就直接使用滑动窗口

Status: Active
First Seen: 2026-08-20
Last Seen: 2026-08-20

### Occurrences

- Session 001 — LeetCode 560

### Correction

先判断窗口扩张或收缩时目标量是否具有足够的单调性；含负数的等和计数问题优先考虑前缀和加哈希。

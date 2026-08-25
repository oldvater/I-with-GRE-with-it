---
schema_version: 1
current_session: 6
current_stage: foundation
last_update: "2026-08-25"
timezone: "Asia/Shanghai"
review_intervals_days: [1, 3, 7, 14, 30, 60]
topics:
  - name: Hash Set
    status: Training
    score: 51
    level: C
    last_training: "2026-08-23"
    next_review: "2026-08-24"
    review_step: 0
    weakness:
      - 能回忆连续序列的哈希起点，但需稳定区分哈希容器与顺序容器的成员查询成本，并独立完成完整复杂度证明
  - name: Prefix Sum
    status: Review
    score: 62
    level: C
    last_training: "2026-08-25"
    next_review: "2026-08-26"
    review_step: 0
    weakness:
      - 能独立完成精确目标和计数与单位置平衡判断，但需继续先区分精确等式和不等式最优化，避免把前缀和加哈希泛化到所有连续区间问题
    difficulty:
      recommended: 1
      confidence: low
      comparable_samples: 2
      recent_indices: [0.93, 0.93]
      last_adjustment: "session006: initialized at 1"
  - name: Sliding Window
    status: Review
    score: 58
    level: C
    last_training: "2026-08-24"
    next_review: "2026-08-27"
    review_step: 1
    weakness:
      - 能独立利用全正数条件证明窗口边界单调性，但需保持边界长度公式准确，并区分含负数时不同目标关系所需的方法
  - name: Binary Search
    status: Review
    score: 58
    level: C
    last_training: "2026-08-22"
    next_review: "2026-08-25"
    review_step: 1
    weakness:
      - 已能独立确定答案变量、判定函数和单调方向，但需用逐项非增关系严谨证明，避免错误的定值乘积论证
  - name: Monotonic Stack
    status: Training
    score: 54
    level: C
    last_training: "2026-08-24"
    next_review: "2026-08-25"
    review_step: 0
    weakness:
      - 已能无提示识别在线跨度的待决状态，并正确排除只求全局最优的假阳性题型；仍需用后续样本确认稳定性并主动写出维护不变量与均摊复杂度
    difficulty:
      recommended: 1
      confidence: medium
      comparable_samples: 4
      recent_indices: [0.56, 1.00, 1.00]
      last_adjustment: "session004: initialized at 1"
  - name: Linked List
    status: Review
    score: 63
    level: C
    last_training: "2026-08-25"
    next_review: "2026-08-28"
    review_step: 1
    weakness:
      - 能独立完成找中点、反转和交叉合并，并在追问后准确说明保存后继的不变量；需在首次解释中主动写出断链、合并终止条件与额外空间
---

# State Notes

Session 001 was backfilled from the 2026-08-20 “算法特训” conversation and archived later.
LeetCode 209 was corrected after the user supplied the complete result: independently AC in 17min with a sound monotonicity explanation.
Session 002 archived the 2026-08-21 Day 2 training: LeetCode 875, 739, and the due review of LeetCode 560.
Session 003 completed the 2026-08-22 three-day diagnostic phase; regular adaptive training begins with the next session.
Session 004 began regular adaptive training: LeetCode 496 and 1475 were optimized after a decisive linearization hint, while LeetCode 128 exposed a Python container-complexity confusion.
Session 005 recorded independent S results on LeetCode 901 and the LeetCode 121 false-positive discrimination task; LeetCode 209 review was independently AC with one boundary typo and one overgeneralized negative-array rule.
Session 006 recorded independent A results on LeetCode 930 and 724 and an A review of LeetCode 143; exact-sum mechanics were fast, while applicability boundaries and proactive invariant explanations remain the next focus.


---
schema_version: 1
current_session: 5
current_stage: foundation
last_update: "2026-08-24"
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
    score: 56
    level: C
    last_training: "2026-08-21"
    next_review: "2026-08-24"
    review_step: 1
    weakness:
      - 已能识别负数会破坏滑动窗口单调性，但需进一步区分等值计数与不等式最优化，避免把含负数问题统一归为前缀和加哈希
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
    status: Training
    score: 60
    level: C
    last_training: "2026-08-22"
    next_review: "2026-08-23"
    review_step: 0
    weakness:
      - 能独立完成反转与重排，需继续严谨说明递归空间复杂度及交叉合并不丢节点的不变量
---

# State Notes

Session 001 was backfilled from the 2026-08-20 “算法特训” conversation and archived later.
LeetCode 209 was corrected after the user supplied the complete result: independently AC in 17min with a sound monotonicity explanation.
Session 002 archived the 2026-08-21 Day 2 training: LeetCode 875, 739, and the due review of LeetCode 560.
Session 003 completed the 2026-08-22 three-day diagnostic phase; regular adaptive training begins with the next session.
Session 004 began regular adaptive training: LeetCode 496 and 1475 were optimized after a decisive linearization hint, while LeetCode 128 exposed a Python container-complexity confusion.
Session 005 recorded independent S results on LeetCode 901 and the LeetCode 121 false-positive discrimination task; LeetCode 209 review was independently AC with one boundary typo and one overgeneralized negative-array rule.


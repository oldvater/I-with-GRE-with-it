---
schema_version: 1
current_session: 4
current_stage: foundation
last_update: "2026-08-23"
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
      - 连续子数组含负数时仍会先尝试基于当前和缩放滑动窗口，需先判断单调性
  - name: Sliding Window
    status: Training
    score: 55
    level: C
    last_training: "2026-08-20"
    next_review: "2026-08-21"
    review_step: 0
    weakness:
      - 能解释正数条件带来的窗口和单调性，但需在含负数和计数型变式中保持算法辨析稳定
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
    score: 44
    level: D
    last_training: "2026-08-23"
    next_review: "2026-08-24"
    review_step: 0
    weakness:
      - 能在明确线性化方向后快速迁移到严格更大与小于等于变式，但无提示时仍先采用逐项后扫，需独立识别待决元素结构并核对目标复杂度
    difficulty:
      recommended: 1
      confidence: low
      comparable_samples: 2
      recent_indices: [0.56, 0.56]
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


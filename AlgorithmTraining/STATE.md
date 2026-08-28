---
schema_version: 1
current_session: 9
current_stage: foundation
last_update: "2026-08-28"
timezone: "Asia/Shanghai"
review_intervals_days: [1, 3, 7, 14, 30, 60]
topics:
  - name: Hash Set
    status: Review
    score: 64
    level: C
    last_training: "2026-08-26"
    next_review: "2026-08-29"
    review_step: 1
    weakness:
      - 能独立区分存在性与次数状态并完成哈希建模；需在首次复杂度说明中严格区分平均 O(1) 查询与线性 O(n) 查询，并明确规模变量
    difficulty:
      recommended: 1
      confidence: low
      comparable_samples: 2
      recent_indices: [1.00, 1.00]
      last_adjustment: "session007: initialized at 1"
  - name: Prefix Sum
    status: Review
    score: 70
    level: B
    last_training: "2026-08-27"
    next_review: "2026-08-28"
    review_step: 0
    weakness:
      - 能独立固定半开前缀定义并完成区间查询，也能辨析中心元素是否排除；需在滚动优化中持续绑定累计量与当前下标，避免 i 与 i+1 的边界计算错误
    difficulty:
      recommended: 1
      confidence: medium
      comparable_samples: 4
      recent_indices: [0.93, 1.00, 0.93]
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
    score: 69
    level: B
    last_training: "2026-08-28"
    next_review: "2026-09-04"
    review_step: 2
    weakness:
      - 能独立完成精确查找、下界查找和答案二分，并已改正定值乘积论证；需用区间不变量证明收敛点满足答案定义，并把单次判定成本乘入总复杂度
    difficulty:
      recommended: 1
      confidence: low
      comparable_samples: 2
      recent_indices: [1.00, 0.93]
      last_adjustment: "session009: initialized at 1"
  - name: Monotonic Stack
    status: Mastered
    score: 59
    level: C
    last_training: "2026-08-27"
    next_review: "2026-08-30"
    review_step: 1
    weakness:
      - 已能无提示识别待决状态、排除全局最优假阳性，并主动写出首次触发不变量与均摊复杂度；后续通过间隔复习保持稳定性
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
Session 007 recorded S results on LeetCode 349 and 350 and an A review of LeetCode 128; Hash Set moved to Review, with complexity terminology retained as the remaining weakness.
Session 008 recorded S/A results on LeetCode 303 and 2574 and an S review of LeetCode 739; Prefix Sum reached level B, while Monotonic Stack met the recent-five graduation rule and moved to Mastered.
Session 009 recorded S/A results on LeetCode 704 and 35 and an A review of LeetCode 875; Binary Search reached level B, while lower-bound invariants and nested-check complexity remain active weaknesses.

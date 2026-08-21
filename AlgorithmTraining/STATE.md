---
schema_version: 1
current_session: 1
current_stage: foundation
last_update: "2026-08-20"
timezone: "Asia/Shanghai"
review_intervals_days: [1, 3, 7, 14, 30, 60]
topics:
  - name: Hash Set
    status: Training
    score: 53
    level: C
    last_training: "2026-08-20"
    next_review: "2026-08-21"
    review_step: 0
    weakness:
      - 能独立识别连续序列的哈希起点，但尚未形成完整的正确性说明
  - name: Prefix Sum
    status: Training
    score: 51
    level: C
    last_training: "2026-08-20"
    next_review: "2026-08-21"
    review_step: 0
    weakness:
      - 连续子数组含负数时仍会先尝试基于当前和缩放滑动窗口，需先判断单调性
---

# State Notes

Session 001 was backfilled from the 2026-08-20 “算法特训” conversation and archived later.
LeetCode 209 had only a partial recoverable attempt, so it did not initialize or change a topic score.

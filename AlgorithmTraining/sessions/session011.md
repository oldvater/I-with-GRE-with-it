# Session 011

Date: 2026-08-30
Timezone: Asia/Shanghai
Current Stage: foundation
Session Status: Completed

## Plan Snapshot

### A — Main Task

Problem: LeetCode 21
Title: Merge Two Sorted Lists
URL: https://leetcode.com/problems/merge-two-sorted-lists/
Source/List: LeetCode
Topic: Linked List
Assigned Weakness: 用哨兵节点稳定处理头结点，并说明已合并前缀、未处理后缀和尾部拼接的不变量
Discrimination Task: No
Task Difficulty: 1
Time Budget: 20min
Selection Reason: Linked List 与 Prefix Sum 同为最早逾期专题，优先选择分数更低的 Linked List 检查基础指针操作。

### B — Variant or Discrimination Task

Problem: LeetCode 203
Title: Remove Linked List Elements
URL: https://leetcode.com/problems/remove-linked-list-elements/
Source/List: LeetCode
Topic: Linked List
Assigned Weakness: 区分修改节点值与真正改变链接，并处理头部删除、连续删除和尾结点删除
Discrimination Task: Yes
Task Difficulty: 1
Time Budget: 15min
Selection Reason: 检验能否根据删除语义选择稳定的前驱视角，并避免对特殊位置逐一打补丁。

### R — Review Task

Problem: LeetCode 143
Title: Reorder List
URL: https://leetcode.com/problems/reorder-list/
Source Session: session006
Topic: Linked List
Original Task Difficulty: N/A
Review Due: 2026-08-28
Selection Reason: 该复习已逾期，需要再次检查断链、反转时保存后继以及奇偶长度下的合并终止条件。

## Results

### A — LeetCode 21

Completion: AC
Result: S
Actual Time: 4min
Independent AC: Yes
Hint Count: 0
Strongest Hint Type: None
Substantial Wrong Approaches: 0
Performance Index: 1.00
Performance Index Quality: Complete

#### Core Reasoning

用户使用 dummy 保存合并链表的入口，因为新头结点不一定来自固定的一条链表。两条链表均非空时比较表头值，把较小节点接到 cur 后并推进对应链表；其中一条耗尽后，将另一条剩余部分整体接到 cur 后。

#### Correctness Explanation

用户说明 cur 之前的链接已经完成，而 list1、list2 及其后继仍属于未处理原链表；每次选择两个当前表头中较小者，得到剩余所有节点中的最小节点，因而保持已合并前缀有序。循环结束时至多一条链表非空，且其表头不小于已合并尾部，所以可整体拼接。dummy.next 保留完整结果入口，已合并前缀无需再次访问。

#### Complexity

- Time: O(m + n)
- Space: 用户未报告；除复用原节点外为 O(1)

#### Wrong Attempts and Pitfalls

- None reported

### B — LeetCode 203

Completion: AC
Result: A
Actual Time: 13min
Independent AC: Yes
Hint Count: 0
Strongest Hint Type: None
Substantial Wrong Approaches: 1
Performance Index: 0.91
Performance Index Quality: Complete

#### Core Reasoning

用户最初计划通过修改节点 val 模拟删除，但发现待删除节点位于队尾时需要特殊处理，随后改用 dummy 保存可能变化的头结点。从前驱节点 cur 的角度检查 cur.next：若其值等于 val，就令 cur.next 越过该节点且不移动 cur；否则推进 cur。

#### Correctness Explanation

用户正确指出删除后不能立即推进，否则会漏掉连续待删除节点。补全不变量为：dummy.next 始终是当前结果入口，cur 是最后一个已经确认保留的节点，cur.next 及其后为待检查部分。删除时只缩短待检查部分而保持 cur；保留时把 cur 推进一位。最终 cur.next 为空时所有节点均已分类，头部、连续和尾部删除都由同一规则覆盖。

#### Complexity

- Time: O(n)
- Space: 用户未报告；除 dummy 和指针外为 O(1)

#### Discrimination Conclusion

题目要求删除节点并保持其余节点原值，因此应修改链接，而不是把值覆盖成别的节点值。dummy 将“删除头结点”统一为普通的“前驱绕过后继”；从前驱检查 next 又能在删除后原地继续处理连续目标值。

#### Wrong Attempts and Pitfalls

- 初始尝试通过修改节点值模拟删除；该方向会改变保留节点的数据，并且无法用同一规则处理尾结点，随后由用户自行放弃。

### R — LeetCode 143

Completion: AC
Result: A
Actual Time: 10min
Independent AC: Yes
Hint Count: 0
Strongest Hint Type: None
Recall Quality: Incomplete

#### Recall and Correction

用户准确回忆并独立完成三阶段结构：快慢指针找中点，用 slow.next = None 分成 l1、l2，反转 l2，再交叉合并。但首次解释仍只说明答案由前半段与后半段反转后合并而成，没有主动写出改指针前保存后继以及奇偶长度下的终止条件。纠正规则是：断链前先保存 l2；反转时先保存 nxt 再改 cur.next；合并时先保存两侧 next 再交叉链接。前半段长度始终不少于后半段，因此以 l2 是否为空作为合并终止条件不会丢节点。

## Ability Update

| Topic | Before | Rating | Delta | After | Evidence |
| --- | ---: | --- | ---: | ---: | --- |
| Linked List | 63 | S | +5 | 68 | LeetCode 21 无提示快速独立 AC，dummy、逐节点合并和尾部拼接均正确 |
| Linked List | 68 | A | +3 | 71 | LeetCode 203 自行放弃修改值的错误方向并完成统一删除，但首次正确性说明未完整陈述不变量 |
| Linked List | 71 | A | +3 | 74 | LeetCode 143 无提示独立 AC，但再次遗漏主动说明后继保存与奇偶长度终止条件 |

## Difficulty Update

| Topic | Before | After | Confidence | Comparable Samples | Reason |
| --- | ---: | ---: | --- | ---: | --- |
| Linked List | N/A | 1 | Low | 2 | 首次获得两个已知 Level 1 的 A/B 样本，PI 为 1.00 和 0.91；样本不足三条，因此初始化并保持 Level 1 |

Recent Comparable Performance Indices: [1.00, 0.91]

## Review Update

| Topic/Problem | Previous Step | Result | Next Step | Next Review |
| --- | ---: | --- | ---: | --- |
| Linked List / LeetCode 21, 203 and 143 | 1 | S / A / A | 2 | 2026-09-06 |

## Mistake Updates

### New — 链表改指针前未主动固定后继可达性与终止不变量

Occurrence: Session 011 — LeetCode 143
Evidence: 用户再次正确 AC，但首次说明没有写出断链、反转和合并前分别保存后继，也没有说明奇偶长度下为何以第二段为空即可安全终止；Session 006 的同题解释也出现过这一遗漏。
Correction: 每次覆盖 next 前先命名并保存仍需访问的后继；同时明确“已处理部分、未处理部分、结果入口”和循环终止时两段长度关系，不能只用目标形状代替指针安全证明。

## Graduation Check

Topic: Linked List
Eligible: No
Recent Five Ratings: Session 003 — LeetCode 143: S; Session 006 — LeetCode 143: A; Session 011 — LeetCode 21: S; Session 011 — LeetCode 203: A; Session 011 — LeetCode 143: A
S Count: 2
D Present: No
Discrimination Task Present: Yes
Decision: Not yet

## Analytics Evidence

- Assigned Tasks: 3
- Completed Tasks: 3
- Independent AC: 3/3
- Reviews Due: 1
- Reviews Completed On Time: 0/1
- New Mistake Patterns: 1
- Recurrences/Reinforcements: 0
- Resolved Patterns: 0

## Next Focus

- 优先处理 2026-08-28 到期的 Prefix Sum 复习，继续检查滚动累计量与下标边界是否严格绑定。
- 随后处理 2026-08-29 到期的 Hash Set 和 2026-08-30 到期的 Monotonic Stack 复习；Linked List 下次复习安排在 2026-09-06。

## Notes

本次按用户明确要求记为 2026-08-30。Linked List 升至 74 分和 Level B，但最近五条有效记录仅有 2 次 S，尚未达到 3 次 S 的毕业条件，因此保持 Review。2026-W35 周报将在进入下一周并归档首个训练会话时生成；本次不跨月，因此不生成月报。

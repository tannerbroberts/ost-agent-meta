---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Have an unattended pass resolve ten seeded merge conflicts and grade every resolution]]

Two agents never write to the same working tree. Each takes a branch, does its whole pass there, and the results are brought together afterwards as an explicit merge that someone or something reviews. Concurrent work is fully supported; concurrent writing to one set of files is not.

Because a vault is append-only Markdown, the merges are unusually well-behaved: two agents appending different sections to different nodes conflict nowhere, and the genuine collisions — two nodes with the same title, two edits to one parent's link list — are exactly the cases that deserve attention.

**Compared to the alternatives.** The only option that lets both agents work at full speed, which a lock cannot. It also matches the tool the vault is already built on. The cost is that merging is a real step someone has to own, and the failure it invites is the one already recorded here: a conflict resolved badly and committed, leaving the next run a repository that cannot build.

**What would make this the wrong pick.** It moves the problem to whoever merges. If that is an unattended pass, the tree has swapped a collision it can detect for a resolution it cannot check, and the second is harder to notice.

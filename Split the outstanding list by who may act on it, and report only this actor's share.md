---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Partition today's sweep by actor and see whether the unattended share is reachable]]

The sweep partitions everything it finds by who is permitted to act. An unattended pass sees what an unattended pass may do. A human sees what needs a human. Nothing is hidden — both partitions are always available — but the default answer to "what is outstanding" is scoped to the asker's authority, and `done` is computed over that share alone.

The vault already holds the information this needs. Lanes say which tests compute may run; the ruleset says which acts require a person; retired nodes are already withheld from one scan while counting for every gate. This applies the same partition to the whole sweep rather than to individual features of it.

**Compared to the alternatives.** No new verb, no new state, and nothing is dropped or forgotten — the partition is derived from permissions the tree already records, so it cannot go stale independently of them. It also does nothing for work that nobody may act on: an item gated for a reason no actor can currently satisfy still sits in someone's partition forever. Acknowledgement and ageing both clear things; this only sorts them.

**What would make this the wrong pick.** A pass that only sees its own share loses sight of what it is blocked behind. There is a real risk of a loop reporting `done` cheerfully while the human partition grows unread, and nothing in this mechanism creates any pressure to look at it.

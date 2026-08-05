---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Partitioning by actor leaves an unattended pass a reachable share and nobody's pile empty]]

The sweep partitions everything it finds by who is permitted to act. An unattended pass sees what an unattended pass may do. A human sees what needs a human. Nothing is hidden — both partitions are always available — but the default answer to "what is outstanding" is scoped to the asker's authority, and `done` is computed over that share alone.

The vault already holds the information this needs. Lanes say which tests compute may run; the ruleset says which acts require a person; retired nodes are already withheld from one scan while counting for every gate. This applies the same partition to the whole sweep rather than to individual features of it.

**Compared to the alternatives.** No new verb, no new state, and nothing is dropped or forgotten — the partition is derived from permissions the tree already records, so it cannot go stale independently of them. It also does nothing for work that nobody may act on: an item gated for a reason no actor can currently satisfy still sits in someone's partition forever. Acknowledgement and ageing both clear things; this only sorts them.

**What would make this the wrong pick.** A pass that only sees its own share loses sight of what it is blocked behind. There is a real risk of a loop reporting `done` cheerfully while the human partition grows unread, and nothing in this mechanism creates any pressure to look at it.

## Definition of done

"Partition today's sweep by actor and see whether the unattended share is reachable"

```
npx vitest run test/ost/sweep-actor-partition.test.ts
```

Red today: nothing partitions the sweep by actor — a sweep item carries no actor field and no classifier produces one. Green when every item lands in one of the four buckets and the nobody-may-act bucket is either empty or fully reasoned.

**The test's prediction has now been checked from the other side.** The node guessed that the stranded evidence records would land in the fourth bucket and that the split would have located the problem without solving it. The 2026-08-05 unattended pass read all twenty-four outstanding evidence items in full: two revealed genuinely new needs and became Opportunity nodes; the other twenty-two corroborated needs the tree already holds. That corroboration was recorded where it belonged, and the twenty-two items still cannot be cleared by any actor on any surface, because `ost_next_work` computes "mapped" from node `source:` frontmatter and only a newly-created node citing the item clears it. So the fourth bucket is not empty, and its contents are not waiting on a person either — they are waiting on a mechanism nobody has built. See the annotation on "An acknowledgement that records a decision not to act, and takes the item off the sweep".

That sharpens what this solution is worth. A partition that reports "nobody may act on these twenty-two" is genuinely useful, because today they are silently counted as the unattended pass's outstanding work and make `done` unreachable. But it is diagnosis, not treatment.

**What this does not settle.** Whether a stated reason is a good reason is a human's judgement; the spec asserts only that one is present. And the node's own second limit stands untouched: a pass shown only its own share may lose sight of what it is blocked behind, and a loop reporting done while the human partition grows unread is a failure this test cannot see.

## History
- 2026-08-05 unlinked "Partition today's sweep by actor and see whether the unattended share is reachable" — moved under "Partitioning by actor leaves an unattended pass a reachable share and nobody's pile empty" — the belief this test measures now has a node of its own

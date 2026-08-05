---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A migration can bring old nodes into compliance without changing what any of them means]]

A rule change is not allowed to land alone. It arrives with a migration that brings existing nodes into compliance where that can be done mechanically, and with a list — node by node — of the ones that cannot, each saying what a human would have to decide. The tree is never left in a state nobody has a plan for.

This puts the cost on the author of the rule, who understands the change and knows what the compliant form looks like, rather than on the operator, who has to reverse-engineer both from a check failure.

**Compared to the alternatives.** The only option that actually resolves the backlog instead of labelling or deferring it, and it keeps a single standard across the whole tree. It is much the most work per rule change, and it will slow tightening down — which may be a feature, since it prices the disruption at the moment the decision is made.

**What would make this the wrong pick.** Automatic migration is a bulk rewrite of a record that is supposed to be append-only. Even done carefully it changes what nodes say without a human reading them, and for a vault whose whole claim is a trustworthy history, that may be too much to hand to a script.

## Test

"Write the migration for one past tightening and have a reader check it changed nothing's meaning"

`npx vitest run test/ost/tightening-migration-meaning.test.ts`

Green when the migration takes a before-tightening tree fixture from red to green under `check` while leaving every node's prose byte-identical. That proves it moved structure, not wording — it does not prove meaning survived, because re-parenting a node changes what its unchanged words claim. The human reader still checks the nodes whose position moved.

## History
- 2026-08-05 unlinked "Write the migration for one past tightening and have a reader check it changed nothing's meaning" — moved under "A migration can bring old nodes into compliance without changing what any of them means" — the belief this test measures now has a node of its own

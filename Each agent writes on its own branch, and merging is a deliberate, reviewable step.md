---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An unattended pass can resolve the merges this creates without corrupting the tree]]

Two agents never write to the same working tree. Each takes a branch, does its whole pass there, and the results are brought together afterwards as an explicit merge that someone or something reviews. Concurrent work is fully supported; concurrent writing to one set of files is not.

Because a vault is append-only Markdown, the merges are unusually well-behaved: two agents appending different sections to different nodes conflict nowhere, and the genuine collisions — two nodes with the same title, two edits to one parent's link list — are exactly the cases that deserve attention.

**Compared to the alternatives.** The only option that lets both agents work at full speed, which a lock cannot. It also matches the tool the vault is already built on. The cost is that merging is a real step someone has to own, and the failure it invites is the one already recorded here: a conflict resolved badly and committed, leaving the next run a repository that cannot build.

**What would make this the wrong pick.** It moves the problem to whoever merges. If that is an unattended pass, the tree has swapped a collision it can detect for a resolution it cannot check, and the second is harder to notice.

## Definition of done

"Have an unattended pass resolve ten seeded merge conflicts and grade every resolution"

`npx vitest run test/git/branch-isolation-merge.test.ts`

The spec asserts both the isolation and the conflict shape the node predicts: two passes never share a working tree; sections appended to different nodes merge without conflict, as append-only Markdown should; and the genuine collisions — two nodes created with the same title, two edits to one parent's link list — surface as conflicts rather than resolving silently. That last clause matters most, because a merge that quietly picks a side is worse than the collision it replaced. Red today because passes write to one working tree.

**What a green here does not settle, and it is where the node says the problem moves.** Whether a resolution is any *good*. The spec proves conflicts are surfaced; grading ten resolutions is the humans-required test, and the node's own warning is that handing the merge to an unattended pass swaps a collision the tree can detect for a resolution it cannot check. This tree already records the downstream failure that produces — "A merge conflict got committed into a source file, so the next run inherits a repo that cannot build" — so the grading is not hypothetical.

## History
- 2026-08-05 unlinked "Have an unattended pass resolve ten seeded merge conflicts and grade every resolution" — moved under "An unattended pass can resolve the merges this creates without corrupting the tree" — the belief this test measures now has a node of its own

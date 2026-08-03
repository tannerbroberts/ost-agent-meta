---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 5 conflicts require human judgement.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that peer exchange is cheap in practice — that two vaults can be merged without a person adjudicating a pile of collisions. If every exchange costs an afternoon of merge work, nobody will do it twice and the federation has no members.

**Risk category: feasibility.**

**Design.** Take the two vaults that already exist and attempt the exchange as a real git merge into a scratch branch. Count: files merging cleanly, files conflicting, and conflicts a person actually has to think about as against ones any rule could settle. Discard the branch.

**Why it is small.** Both vaults exist, the merge is one command, and nothing is kept.

**What it will not cover.** These two vaults share an author, a schema version, and a naming style. Two vaults from unrelated teams would collide far more, and this is the easiest possible case.

A human runs this and records the result.

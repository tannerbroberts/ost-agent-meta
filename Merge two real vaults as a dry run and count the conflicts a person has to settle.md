---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 5 conflicts require human judgement.
instrument: npx vitest run test/ost/vault-merge-conflict-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that peer exchange is cheap in practice — that two vaults can be merged without a person adjudicating a pile of collisions. If every exchange costs an afternoon of merge work, nobody will do it twice and the federation has no members.

**Risk category: feasibility.**

**Design.** Take the two vaults that already exist and attempt the exchange as a real git merge into a scratch branch. Count: files merging cleanly, files conflicting, and conflicts a person actually has to think about as against ones any rule could settle. Discard the branch.

**Why it is small.** Both vaults exist, the merge is one command, and nothing is kept.

**What it will not cover.** These two vaults share an author, a schema version, and a naming style. Two vaults from unrelated teams would collide far more, and this is the easiest possible case.

A human runs this and records the result.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/vault-merge-conflict-census.test.ts — The threshold — at most 5 conflicts require human judgement — becomes machine-checkable once conflicts are classified: the spec merges the two vault fixtures into a scratch tree, partitions every conflict into ones a stated rule settles and ones it cannot, and asserts the judgement-requiring count is at most 5. It fails today because nothing merges two vaults or classifies what a rule could settle.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/vault-merge-conflict-census.test.ts` — No test files found, exiting with code 1
- 2026-08-22 **green** (exit 0) `npx vitest run test/ost/vault-merge-conflict-census.test.ts` — Duration  18.24s (transform 36ms, setup 0ms, collect 53ms, tests 17.98s, environment 0ms, prepare 36ms)

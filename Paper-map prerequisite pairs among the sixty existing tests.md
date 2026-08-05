---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/ost/test-prerequisite-edges.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (desirability):** real test sets contain enough genuine dependencies to be worth a schema and validator change.

**Method:** human with a printout of all 60 AssumptionTest titles marks genuine A-blocks-B pairs (B is unrunnable or uninterpretable until A lands). A few hours, zero build.

**Pre-committed threshold:** >= 10 genuine prerequisite pairs among the current 60, else the schema change dies here.

**Decides:** prerequisite edges vs a simple rank/route view (sibling 'Rank every node by how many blocked tests one build would unblock').

*Proposed by the agent-side hard-fix pass — to be run by a human. No results recorded here.*

## History
- 2026-07-24 evidence: (none) → assertion — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
- 2026-08-05 instrument: (none) → npx vitest run test/ost/test-prerequisite-edges.test.ts — A paper map is thrown away unless the tree can hold what it found, and there is nowhere to put a prerequisite pair today — the count has since grown from sixty to 272, so a map drawn by hand and left on paper is wasted twice over. This asserts the structure: an AssumptionTest can declare another test as its prerequisite, a cycle between two tests is refused, and the sweep does not offer a test whose prerequisite has no result yet — reporting it as blocked instead. Missing-spec red, not assertion red: the pass cannot read the repo, so the file is absent; a builder should write it against the real test schema and sweep so it goes red on a prerequisite the sweep currently ignores. It does not settle which pairs are prerequisites of which — that reading of 272 tests is the human's paper map, and this only gives it somewhere to land.

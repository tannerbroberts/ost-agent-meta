---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/ost/branch-provenance-warning.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** A stated propagation rule ranks branches by trustworthiness in a way informed humans recognise as fair.

**Proposed test:** Write the rule down on paper. Have three reviewers independently rank eight branches of the current tree from most to least trustworthy, without seeing the rule. Compare each ranking against the rule's output.

**Size:** an hour per reviewer; no code, uses the tree as it stands today.

**Pre-committed threshold:** at least 2 of 3 reviewers agree with the rule on both the top three and the bottom three branches. Disagreement in the middle is acceptable; disagreement at the extremes means the rule would mis-rank exactly the branches people act on.

**Decides:** whether propagation can be automated at all, or whether trustworthiness stays a human judgement the tree merely displays.

Proposed by the agent — to be run by a human with real reviewers. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/ost/branch-provenance-warning.test.ts — Asserts the half of this node that is not yet built: a branch whose sources are all internal — founder note, agent ideation, or a self-generated channel — is flagged as having no external source wherever the branch is read. Red against today's output rather than a missing file: the weakest-rung roll-up already ships and reports "rests on assertion" with a source count per bucket, but nothing distinguishes fourteen internal sources from one outside voice, so the node's own example warning "this opportunity has no non-founder source" cannot currently be emitted.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/branch-provenance-warning.test.ts` — No test files found, exiting with code 1

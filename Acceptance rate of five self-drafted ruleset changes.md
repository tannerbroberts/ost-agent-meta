---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/knowledge/ruleset-proposal.test.ts
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability, with a usability half):** The changes the agent proposes to its own rules are ones a human would accept — and reviewing one is genuinely cheaper than writing it.

**Proposed test:** Have the agent draft five workflow changes from friction it has actually logged, each with the evidence attached. A human reviews each, marks it accept / accept-with-edits / reject, and notes the review time. For two of the accepted ones, the human also estimates how long writing it from scratch would have taken.

**Size:** one drafting pass plus an hour of review.

**Pre-committed threshold:** ≥2 of 5 accepted as-is or with minor edits AND median review time under 5 minutes AND clearly below the write-from-scratch estimate. Proposals that take as long to review as to write have no reason to exist.

Proposed by the agent — a human does all reviewing and accepting. The agent must never adopt its own proposal. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/knowledge/ruleset-proposal.test.ts — Asserts the safety property that makes this candidate never surprise the operator: a pending proposal does not alter the ruleset the pass actually executes, and every proposal carries the friction evidence ids that triggered it. Red today because the agent has no way to draft a change to its own ruleset — the ruleset is generated from source and only a human edits it.

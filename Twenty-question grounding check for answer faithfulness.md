---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/mcp/status-answer-faithfulness.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility, and the highest-harm assumption in this branch):** Answers stay faithful to the tree — every claim traceable to a node, nothing invented, and "we don't know" said plainly when the tree is silent.

**Proposed test:** Write twenty questions whose correct answers are known from the current tree, including five the tree genuinely cannot answer. Ask them. A human checks every claim against the cited node.

**Size:** an hour of question-writing and an hour of checking.

**Pre-committed threshold:** ≥19 of 20 answers fully grounded with correct citations AND zero invented claims AND all five unanswerable questions answered with an explicit "the tree doesn't say." Any fabrication fails the test outright — a status surface that invents evidence attacks the outcome it is meant to serve.

Proposed by the agent — a human must do the grounding check; the agent must not verify its own citations. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/mcp/status-answer-faithfulness.test.ts — Faithfulness has a mechanical form here because the ground truth is the tree itself — commit twenty questions whose correct answers are derivable from a fixture vault, ask the status surface each one, and assert every answer matches and cites a node that exists; it fails today because no conversational status surface exists to answer them.

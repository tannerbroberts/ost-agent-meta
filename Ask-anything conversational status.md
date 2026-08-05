---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Free-form questions about the tree can be answered faithfully from the tree]]

Let a stakeholder simply ask — "what's the strongest evidence we have?", "what changed this week?", "why is this branch still unvalidated?" — and get an answer grounded in the tree, with links to the nodes it came from.

**How it differs from its siblings:** meets the stakeholder's actual question instead of a fixed layout, and scales as the tree grows because nobody has to read all of it. No format to learn.

**Trade-off:** an answer that sounds confident can smuggle in unsourced claims — exactly the failure this outcome exists to prevent — so grounding and citation are non-negotiable.

**Riskiest assumptions to test:** that answers stay faithful to the tree with no invented content (feasibility); that stakeholders think to ask rather than waiting to be told (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Twenty-question grounding check for answer faithfulness" — moved under "Free-form questions about the tree can be answered faithfully from the tree" — the belief this test measures now has a node of its own

## Test

"Twenty-question grounding check for answer faithfulness"

`npx vitest run test/mcp/status-answer-faithfulness.test.ts`

Green when all twenty committed questions are answered correctly against a fixture vault and every answer cites a node that exists. Faithfulness on a known set only — the questions a real operator brings are the ones with no ground truth. The citation assertion is the half that generalises, because a confident answer about a node the tree lacks is the failure that would end trust fastest.

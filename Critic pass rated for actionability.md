---
type: AssumptionTest
status: unvalidated
evidence: assertion
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability, with a usability constraint):** An independent critic surfaces objections a human agrees are worth acting on — and few enough of them to read.

**Proposed test:** Run one critic pass over the current opportunity set. Hand a human the raw list, unfiltered, and have them mark each objection "worth acting on" or "noise" without seeing which node it came from.

**Size:** one pass of compute plus 30 minutes of rating.

**Pre-committed threshold:** ≥40% of objections rated worth acting on AND the total list is ≤20 items. A high hit rate buried in 60 objections fails — an unread critic is not a critic.

**Decides:** whether adversarial review earns a standing slot in the maintenance loop.

Proposed by the agent — the rating must be done by a human; the agent must not grade its own critic. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

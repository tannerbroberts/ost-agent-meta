---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test does the LLM judge agree with human faithfulness ratings]]

**Candidate solution (unvalidated).** A judge model — independent of the proposer — rates every node on whether it is genuinely grounded in its cited evidence and correctly shaped (opportunity as need, not solution). Produces a per-run faithfulness score without needing hand-built fixtures.

**Approach:** *automated grounding check by a separate model* (proposer ≠ judge).

**Contrast with siblings:** unlike the golden set it needs no curated answers and scales to arbitrary evidence; unlike human sampling it is cheap and continuous but is itself a model whose judgment must be spot-checked.

_Addresses: "Can't tell if the generated tree is actually any good". Also supports "Worry the agent is grading its own homework". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

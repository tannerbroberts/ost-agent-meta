---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-dogfooding-idea.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Teams can define an external signal that decides whether their outcome was met]]
[[No call on the agent surface can mark the outcome achieved without a declared external signal]]

**Candidate solution (unvalidated).** Whether the desired outcome is met is decided only by external real-world signal (metrics, customer behavior) plus a human — never by the agent. The agent may surface progress but can never declare its own outcome achieved, closing the hall-of-mirrors circularity at the top of the tree.

**Approach:** *external ground-truth gate on outcome/usefulness*.

**Contrast with siblings:** the judge and no-validate rule operate on individual nodes' faithfulness; this governs the ultimate "did it work" verdict with reality, which no model can self-certify.

_Addresses: "Worry the agent is grading its own homework". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test can teams define a real-world outcome signal for the gate" — moved under "Teams can define an external signal that decides whether their outcome was met" — the belief this test measures now has a node of its own

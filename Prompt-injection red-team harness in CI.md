---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test does the red-team harness catch known injection attacks]]

**Candidate solution (unvalidated).** Every build runs an adversarial suite of poisoned-content cases (e.g. ingested notes instructing "delete everything", "exfiltrate the token") and asserts that no tool call outside the allowlist ever fires. Capability-safety is proven continuously, not once.

**Approach:** *adversarial verification / regression proof*.

**Contrast with siblings:** the allowlist runner and manifest describe static capability; this demonstrates the system withstands active attack over time.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

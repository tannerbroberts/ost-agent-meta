---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test does the red-team harness catch known injection attacks]]

**Candidate solution (unvalidated).** Every build runs an adversarial suite of poisoned-content cases (e.g. ingested notes instructing "delete everything", "exfiltrate the token") and asserts that no tool call outside the allowlist ever fires. Capability-safety is proven continuously, not once.

**Approach:** *adversarial verification / regression proof*.

**Contrast with siblings:** the allowlist runner and manifest describe static capability; this demonstrates the system withstands active attack over time.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test do operators actually replay the audit trail to regain trust]]

**Candidate solution (unvalidated).** Every change the agent makes is an atomic git commit carrying the node, its provenance link, and a human-readable message. After walking away, the operator rebuilds trust by replaying the diff history — nothing is hidden, everything is attributable to a source.

**Approach:** trust via *transparency / verifiability after the fact*.

**Contrast with siblings:** unlike the proactive digest (push) this is pull/inspect-on-demand; unlike guided-trial (earn trust before) this earns trust continuously by leaving an auditable record.

_Addresses: "Trust an unmonitored agent enough to walk away". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

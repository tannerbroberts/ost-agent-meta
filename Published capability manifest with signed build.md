---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test does a published manifest increase operator trust]]

**Candidate solution (unvalidated).** Publish the exact list of tools the agent can call as an inspectable manifest, and ship signed releases so an operator can verify the running binary matches the audited tool set. Proof is *inspectable*, not just asserted.

**Approach:** *verifiable transparency* about capability.

**Contrast with siblings:** the allowlist runner makes the claim true; this lets a skeptical operator confirm it without reading source; the red-team harness stress-tests it dynamically.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

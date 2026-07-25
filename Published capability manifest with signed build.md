---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test does a published manifest increase operator trust]]

**Candidate solution (unvalidated).** Publish the exact list of tools the agent can call as an inspectable manifest, and ship signed releases so an operator can verify the running binary matches the audited tool set. Proof is *inspectable*, not just asserted.

**Approach:** *verifiable transparency* about capability.

**Contrast with siblings:** the allowlist runner makes the claim true; this lets a skeptical operator confirm it without reading source; the red-team harness stress-tests it dynamically.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

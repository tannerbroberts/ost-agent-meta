---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault
[[Allowlist Tool Runner registers only OST tools]]
[[Prompt-injection red-team harness in CI]]
[[Published capability manifest with signed build]]

**Customer need (operator's perspective):** "I don't want to rely on the agent *choosing* to behave, or on a blocklist that might miss something. I want assurance that no general-purpose or destructive capability even exists for a poisoned input to hijack — trust from the absence of capability, not from restraining a capable agent."

The pain is distrust of restraint-based safety: an operator worries a capable agent held back by rules can still be talked into misbehaving. They want confidence that the dangerous tool simply isn't present.

**Litmus (more than one way to address?):** Yes — allowlist-only tool runner, capability-scoped runtimes, minimal-tool agents, verified sandboxes, etc.

_Provenance: INBOX:2026-07-22-runtime-decision.md (implementation decision, 2026-07-22). NOTE: the evidence is solution-rationale-shaped (Tool Runner allowlist vs Agent SDK blocklist); reframed here to the underlying operator need. Closely related to "Fear the agent could take a destructive, irreversible action" — flagged for possible human merge. Unvalidated — for human review._

## Issues
- 2026-07-24 Possible duplicate / merge candidate: this opportunity overlaps substantially with sibling "Fear the agent could take a destructive, irreversible action". Both express the operator's safety-trust need; this one emphasizes assurance via *absence of capability* (allowlist Tool Runner) while the sibling emphasizes *revertible worst case even under prompt injection*. Source evidence (runtime-decision) is solution-rationale-shaped and was reframed into a need. A human should decide whether to keep these as distinct facets or merge them into one opportunity.

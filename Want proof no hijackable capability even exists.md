---
type: Opportunity
status: deferred
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Allowlist Tool Runner registers only OST tools]]
[[Published capability manifest with signed build]]

**Customer need (operator's perspective):** "I don't want to rely on the agent *choosing* to behave, or on a blocklist that might miss something. I want assurance that no general-purpose or destructive capability even exists for a poisoned input to hijack — trust from the absence of capability, not from restraining a capable agent."

The pain is distrust of restraint-based safety: an operator worries a capable agent held back by rules can still be talked into misbehaving. They want confidence that the dangerous tool simply isn't present.

**Litmus (more than one way to address?):** Yes — allowlist-only tool runner, capability-scoped runtimes, minimal-tool agents, verified sandboxes, etc.

_Provenance: INBOX:2026-07-22-runtime-decision.md (implementation decision, 2026-07-22). NOTE: the evidence is solution-rationale-shaped (Tool Runner allowlist vs Agent SDK blocklist); reframed here to the underlying operator need. Closely related to "Fear the agent could take a destructive, irreversible action" — flagged for possible human merge. Unvalidated — for human review._

## Issues
- 2026-07-24 Possible duplicate / merge candidate: this opportunity overlaps substantially with sibling "Fear the agent could take a destructive, irreversible action". Both express the operator's safety-trust need; this one emphasizes assurance via *absence of capability* (allowlist Tool Runner) while the sibling emphasizes *revertible worst case even under prompt injection*. Source evidence (runtime-decision) is solution-rationale-shaped and was reframed into a need. A human should decide whether to keep these as distinct facets or merge them into one opportunity.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-07-25 status: unvalidated → deferred — Human-authorized merge (2026-07-24): self-flagged near-duplicate of sibling 'Fear the agent could take a destructive, irreversible action' — same fear, two mitigation philosophies; every listed alternative is the same mechanism. Its three solutions are now also linked under the surviving sibling. Deferred, never deleted; reverse by resetting status.
- 2026-07-25 Merged into 'Fear the agent could take a destructive, irreversible action' (2026-07-24, human-authorized). Solutions relinked under the survivor; this node deferred. The capability-absence-vs-restraint distinction it carried now lives in the survivor's solution set.
- 2026-08-05 unlinked "Prompt-injection red-team harness in CI" — this solution asserts that poisoned content — an ingested note saying 'delete everything' — fires no tool call outside the allowlist, which is the destructive-action need's own stated case rather than a claim about which capabilities exist — one node, one parent

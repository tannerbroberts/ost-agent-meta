---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

A command that inspects the current session against the vault and reports the specific gap: which file is absent, what one line it needs, and where it belongs. The root cause in the observed case took four passes and a comparison against a sibling example vault to locate, and it is mechanically checkable in under a second.

**Compared with the alternatives:** this fixes the existing vaults that setup-time configuration cannot reach, and it is honest about ownership — it tells the operator what to do rather than editing their configuration for them. Its weakness is that it only helps someone who thinks to run it, which is not the person currently losing four scheduled passes in silence. It is the cheapest of the three to build and the one most dependent on being invoked at the right moment.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

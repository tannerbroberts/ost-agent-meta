---
type: Assumption
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Every solution in the current backlog has an existing spec that could go red for it]]

**Kind: feasibility.**

**The belief, stated so it could be false.** The refusal is only defensible if an author can always name an *existing* spec whose assertions would go red for the behaviour in question. For a change inside a module that already has a spec, that is easy. For behaviour with no existing home — a new tool verb, a new lane, a new report — there may be no honest existing file to point at, and the rule then forces either a lie (pointing at an unrelated spec) or an escape hatch that swallows the rule.

**What would make it false.** A solution in the current backlog for which no existing spec file in the product suite could be made to go red without misfiling it.

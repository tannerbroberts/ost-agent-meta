---
type: Assumption
source: 'agent-ideation:2026-08-10-unattended-sweep'
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Feasibility.** The whole mechanism rests on there being a knowable denominator: a list of the tool names the host can hand an unattended pass, committed in this repository, against which the grant and the deny list can be reconciled. If that set cannot be obtained — or churns fast enough that the committed copy is wrong most weeks — then the check does not prove exhaustiveness, it proves agreement with a stale file, and a capability could arrive and sit unaccounted for exactly as `Read`, `Glob` and `Grep` do today.

Stated so it can be false: *the host's built-in tool set can be enumerated from something committed, and it changes rarely enough that a red build means a real decision is owed rather than a manifest needing a bump.*

The evidence cuts both ways and is worth writing down before anyone tests it. Against: the script already records two renames inside a few weeks — `SlashCommand` retired in favour of `Skill`, `MultiEdit` folded into `Edit` — so the surface demonstrably moves, and one of those moves opened a hole. For: both of those were *visible* as warnings on every firing ("Permission deny rule "SlashCommand" matches no known tool"), which means the host does report the mismatch already and a manifest check would have converted that noise into a failure the first time it printed.

If this turns out false, the fallback is not the sibling solutions — it is to stop asserting exhaustiveness at all and say plainly that the containment covers a named list of capabilities and no more, which is what the deny list's own predicate comment already says and what `docs/reference/v1-readiness.md` P10 already declines to claim.

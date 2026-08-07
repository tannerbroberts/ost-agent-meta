---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** `ost_set_instrument` refuses when the test already carries a command, unless the call explicitly says replacement is intended. The refusal names the existing command, so the pass learns what it was about to destroy at the moment it matters.

**Why this shape.** It is the same guard the tree already applies where a write would clear a gate nobody earned: `ost_link_nodes` refuses to attach a node carrying a recorded result to a new parent, and `ost_merge_nodes` refuses to fold a result-carrying node into one without. Replacing an instrument un-clears a permit by the tool's own contract, which puts it in exactly that family — and it is the one member of the family with no guard.

Unlike its informational sibling, this cannot be ignored under budget pressure, because the write does not happen.

**How it compares to its siblings.**
- "The sweep reports which tests already carry an instrument" informs; this refuses. Refusing is the stronger guarantee and the one that survives a pass that skims.
- "Replacing an instrument preserves the old command and re-arms the permit if it is restored" is about recovery rather than prevention, and would have helped the case that actually happened — this one would have prevented it.

**Where it fails, stated so it can be judged.** Every mandatory flag becomes a flag that is always passed. A pass working a large backlog learns in one iteration that the refusal is cleared by adding a parameter, and from then on the guard costs a round trip and stops nothing. Whether that happens is the assumption beneath this node, and it is the reason the refusal message should name the existing command rather than name the flag — the useful content is the thing being destroyed, not the way past the door.

It also collides with legitimate correction. Fixing a wrong instrument is the same call shape as clobbering a good one, and the tool cannot tell them apart from the arguments alone.

**Cost.** A parameter, a refusal path, and fixtures for both directions.

⚠️ Unvalidated. Agent-ideated.

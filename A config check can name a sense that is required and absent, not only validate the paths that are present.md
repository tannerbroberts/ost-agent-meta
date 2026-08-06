---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Load this vault's own config and require the check to name product.repos as absent]]

Feasibility, and it is the one that decides whether this candidate catches the case that motivated it.

Validating declared paths is easy: iterate the keys that hold paths, stat each, report the misses. That is not what went wrong here. `product.repos` is **absent** — not empty, not pointing somewhere wrong — so there is no path to validate and a present-paths check sails straight past it.

The belief is that absence is detectable without asking the operator to declare intent twice: specifically, that a config naming a repository under one key (`adapters.transcript.projectDir`) while `product.repos` is missing is a recognisable, reportable shape.

Stated so it can be false: it may not be recognisable. An operator can legitimately want transcript harvesting from a directory the agent should not read as a product. If so, the check either nags every correctly-configured vault or needs an explicit "senses I intend to use" declaration — which is a schema change and a setup burden, and moves the cost to exactly the person this was meant to spare.

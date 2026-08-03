---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Count how many existing rules would need a conditional to support two live versions]]

A vault records the ruleset version it is on. Checks evaluate against that version, so a tightening published today does not retroactively fail a tree that has not adopted it. Adopting is an explicit act: the operator moves the version, sees exactly what newly fails, and does that work when they choose to.

Control is the point. The operator decides when to take a tightening, in the same way they decide when to take a dependency upgrade, and until they do their gate keeps telling them the truth about the standard they are actually held to.

**Compared to the alternatives.** Puts the operator in charge of the timing without exempting anything permanently, and it makes adoption a visible decision with a visible cost rather than an ambush. It also allows a tree to sit on an old ruleset indefinitely, and it means the check's meaning now depends on a version — two vaults reporting clean are not necessarily held to the same standard.

**What would make this the wrong pick.** Versioned rules multiply. Every rule must keep working under every version anyone is still on, and the checking code accumulates conditionals for standards nobody has used in months — a maintenance cost paid forever for a disruption that happens occasionally.

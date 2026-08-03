---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Pick the floor deliberately — bash 3.2, because that is what macOS ships — and enforce it where the script is written rather than where it is run. A linter configured to that floor rejects `mapfile` and everything like it at authoring time, in the same place every other coding standard is enforced.

This moves the discovery to the earliest possible moment, which is neither install nor run but the commit that introduced the incompatibility, when the person who wrote it is still looking at it.

**Compared to the alternatives.** Catches the problem before it can reach any machine, needs no manifest to be maintained, and cannot be defeated by an undeclared dependency, since the linter reads what the script actually does. It constrains the author permanently to an old dialect, which is a real ongoing cost, and it protects only against version drift — a missing command that exists at every version is invisible to it.

**What would make this the wrong pick.** Choosing the floor is a guess about every machine the helper will ever run on. Set it too low and the code is worse than it needs to be forever; set it where the evidence pointed and the first Linux container with a different shell entirely is outside the guarantee.

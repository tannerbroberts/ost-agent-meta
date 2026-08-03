---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

A vault-scoped lock taken before any mutation and released after it commits. A second agent arriving finds the lock, learns who holds it and since when, and waits rather than proceeding. Concurrent writes stop being possible instead of being handled.

The evidence for needing something at this level is that the detection route has already failed in practice: an agent discovered another writer only when its own edit missed, by which point fourteen files had changed under it and a merge conflict had been committed into a source file.

**Compared to the alternatives.** The simplest thing that actually works, and the easiest to reason about — there is no merge semantics to get right because there is never anything to merge. It also serialises everything, including writes that would never have collided, and a lock left behind by a crashed run blocks the vault until someone clears it. Detecting drift at write time is more permissive and much more fiddly.

**What would make this the wrong pick.** Locks and unattended runs are an uncomfortable pairing. Every stale-lock recovery policy is either too eager, in which case it defeats the lock, or too patient, in which case a crash on Friday costs the weekend.

---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Crash a run holding the lock and time how long the vault stays unusable]]

A vault-scoped lock taken before any mutation and released after it commits. A second agent arriving finds the lock, learns who holds it and since when, and waits rather than proceeding. Concurrent writes stop being possible instead of being handled.

The evidence for needing something at this level is that the detection route has already failed in practice: an agent discovered another writer only when its own edit missed, by which point fourteen files had changed under it and a merge conflict had been committed into a source file.

**Compared to the alternatives.** The simplest thing that actually works, and the easiest to reason about — there is no merge semantics to get right because there is never anything to merge. It also serialises everything, including writes that would never have collided, and a lock left behind by a crashed run blocks the vault until someone clears it. Detecting drift at write time is more permissive and much more fiddly.

**What would make this the wrong pick.** Locks and unattended runs are an uncomfortable pairing. Every stale-lock recovery policy is either too eager, in which case it defeats the lock, or too patient, in which case a crash on Friday costs the weekend.

## Definition of done

[[Crash a run holding the lock and time how long the vault stays unusable]]

```
npx vitest run test/git/stale-lock-recovery.test.ts
```

Green means a holder killed in each of the four shapes the test names — clean exit, hard kill, hung-but-still-holding, machine sleep — leaves the vault usable again inside fifteen minutes, and recovery never once released a lock that was still genuinely held. Both bars are the node's own, fixed before any run. It is red today because there is no lock and no recovery policy.

**Why the recovery half is the definition of done and the locking half is not.** Taking a lock is trivial and every implementation does it correctly. Every way this solution actually fails is a recovery policy that is wrong in one of two directions — too eager and it defeats the lock it just added, too patient and a crash on a Friday costs the weekend. A spec that only proved mutual exclusion would go green on a design that makes the vault worse than no lock at all.

**What green does NOT settle.** A hung holder and a crashed one are indistinguishable from outside, and no policy resolves that — the command measures the cost of choosing wrongly in each direction, it does not find a choice with no cost. Picking the timeout stays a human's call. It also says nothing about whether operators would accept waiting at all, which is the desirability question underneath the whole candidate and belongs to a person.

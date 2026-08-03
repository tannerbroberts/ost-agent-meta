---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Do not try to preserve done-ness. Make the reinterpretation impossible to miss: when a build reads a vault last written under a different accounting, it says so — "27 outstanding, of which 18 were counted done under the previous version" — and names them, so the reopened class is distinguishable from the genuinely outstanding one.

**The trade it makes:** it addresses the part of the need the other two do not. The stated cost here was never only wasted passes; it was that *"there is no way to tell that class of item apart from work that really is"* outstanding. Separating the two classes is the whole ask, and it needs no migration, no guessing, and no permanent write. The price is that the work is still reopened — an operator now knows why the number moved but still has to disposition eighteen items by hand.

**How it differs from its siblings.** The other two make the count *right*. This one makes the count *explicable*, which is a different and more modest claim: that the operator can be trusted to resolve the discrepancy once they can see it. It is also the only one that stays correct when the migration would have guessed wrong, because it never asserts anything about the past — it only reports that two answers exist.

**It composes rather than competes.** Migration plus this reporting is a strictly better pair than migration alone, because the migration entry becomes readable rather than silent. If a human picks a migration route, this should probably ship with it.

Distinguishing assumption: that the build can tell it is looking at a vault written under different accounting. If nothing in the vault records which version last wrote it, there is no boundary to report and this cannot fire — which makes a version stamp the real precondition for all three siblings.

---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  A merge preceded by a fetch whose result was discarded must succeed, and a
  merge with no prior fetch must be refused. Both must hold; either outcome on
  the first assertion is informative, but a guard that also permits the no-fetch
  merge fails the test outright.
instrument: npx vitest run test/tools/merge-read-guard-bypass.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Try to defeat the guard rather than confirm it. In one session, fetch the survivor's body, discard it without reading, and immediately call the merge with prose composed from the title alone. If the merge succeeds, the assumption holds and the guard is exactly as weak as claimed — which is the finding, and it is a reason to prefer the patch-shaped candidate that needs no guard.

Assert the same in the other direction: a merge with no prior fetch in the session is refused. Without that half, a guard that never fires would also pass the first assertion.

## Why the finding is useful either way

A pass tells you the guard is a formality and the sibling solution is the better buy. A fail tells you the guard is stronger than expected — that satisfying it requires something a caller cannot trivially fake — and this solution deserves more weight than its own node currently gives it.

## What this does not settle

Whether real callers take the shortcut, which is behavioural and needs observation of actual passes rather than a spec. This establishes only that the shortcut is available.

## Instrument grounding

Weak red: the spec file is absent, so the command fails for want of a file rather than against a real module. Written without repository sight (`ost_read_repo` refused for want of `product.repos`). Tracked as "My instruments are red because a file is absent, not because the behaviour is".

## Lane

Not declared. Mechanical question; the lane is a human's to set with `ost-agent lane --set`.

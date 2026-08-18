---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Resetting to main before reading which script to run only avoids the "unreviewed policy" problem if no concurrent or overlapping firing is relying on the current, possibly-modified checkout state at that moment. If firings can overlap in time on the same shared checkout, a hard reset could destroy another firing's in-progress work rather than just its own stale script selection.

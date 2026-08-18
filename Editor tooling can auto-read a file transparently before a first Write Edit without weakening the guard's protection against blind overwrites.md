---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

The guard exists to stop a session from overwriting content it never looked at. Auto-reading on the session's behalf only preserves that protection if the auto-read genuinely happens first and its content is what the session's subsequent edit is computed against — not a stale or partial read inserted after the edit was already planned. If the harness can't guarantee ordering, "auto-read" could silently become "assume it's fine," which is the failure mode the guard was built to prevent.

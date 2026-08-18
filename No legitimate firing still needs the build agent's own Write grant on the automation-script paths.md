---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Ask the operator whether any firing has legitimately needed to edit its own automation scripts mid-run]]

Locking the build agent out of writing its own automation scripts only works if no future firing has a legitimate reason to adjust those scripts as part of finishing a real build task. If some firings do need that (e.g. fixing a broken build step they just discovered), denying the grant outright would convert a policy problem (unreviewed self-edits) into an availability problem (stuck firings) instead of solving it.

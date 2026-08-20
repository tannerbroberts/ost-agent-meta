---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Replaying the PR #130 sequence, the preflight refuses the third selection of a twice-red unchanged target]]

**Kind: feasibility, and the record already argues against it.** The "has not shipped after 2 attempt(s) in a row" note proves the loop can count attempts *somewhere*. But the same target was selected a third time on 2026-08-19, after two identical notes and after a human had set the solution `deferred` — so either the count is reset (a fresh clone, a state directory outside the vault that did not persist, a node-hash comparison that saw an unrelated change), or selection never reads it. `examples/automation/build-pass.sh`'s preflight, read this pass, computes the buildable list from `gate` and `buildable` alone; no per-target history appears in the selection path the script shows. The tree already holds the question from another angle — "Ask someone with the build loop's source and persisted state open whether a per-target failure record already exists across firings" — and it is unanswered.

**Stated so it could be false:** given the recorded sequence for PR #130 (two firings, both ending on the same failing assertion, node file unchanged), a third selection of that target is refused by the preflight.

**What would change if it were false.** The solution needs to *create* the persistent count, not merely consult it — which is more work and means the stuck-note mechanism and this one would be two records of one fact unless they share a file.

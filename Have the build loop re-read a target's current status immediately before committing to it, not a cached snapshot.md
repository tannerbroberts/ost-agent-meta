---
type: Solution
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

If the loop selects candidates from a list built earlier in its run (or carried over from a prior firing) and does not re-check the node file at the moment it commits to building one, a status change written between selection and commit is invisible to it. Fix: re-read the target node's frontmatter (status at minimum) as the last step before starting work, and skip to the next candidate if it has changed.

**Why this reading fits the evidence better than a missing filter would.** The third build-loop report claims "the vault node was never updated after the first two runs" — which is false; it was updated on 2026-08-16, before the second and third re-selections. A loop that had simply never filtered on status would not need to make that (incorrect) claim about the node being unchanged; it would just not care about status at all. A loop reading a stale copy would genuinely see an unchanged node and say so honestly, while being wrong about the live file. This candidate targets that specific failure.

**What would make this the wrong pick.** If the loop has no caching layer at all and reads fresh every time, this fix is a no-op and the real bug is the missing filter (see the sibling solution).

⚠️ Unvalidated. Proposed by an unattended pass; distinguishing this from the sibling requires reading the build loop's own source, which this pass could not do (repo sight unavailable).

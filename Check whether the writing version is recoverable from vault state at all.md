---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  The writing version is recoverable for at least 95 of the last 100 vault
  states in git history.
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, and it is a precondition for the whole row rather than for this candidate alone.** Nothing here can fire unless a build can tell it is looking at a vault written under different accounting. If the vault does not record which version last wrote it, there is no boundary to detect — migration cannot know when to run, the fallback cannot know when to stop, and this candidate has nothing to report.

**The test.** Walk the last hundred commits of the vault. For each state, try to determine the writing version from what is on disk — a stamp if one exists, and failing that from inferable signals: which state files are present, which frontmatter fields, which commit-message formats the tools produce. Count how many are unambiguous.

**Why it should be run first in this row.** It is the cheapest test here, needs no new code beyond a read-only walk, and a failure re-scopes all three siblings at once: if the version is not recoverable, the row's real first move is to *start stamping it*, and every candidate above is blocked behind that. Finding out a row is blocked is a valid and valuable result.

**Why 95 and not 100.** The earliest commits predate most conventions and are allowed to be ambiguous — they are history, not a live migration target. A gap in the recent tail would be disqualifying and this threshold would catch it, since 5 misses cannot cover a recent run.

**What it would produce as a by-product.** A dated map of when the accounting actually changed, which is what any of the three siblings needs in order to state the boundary in a message a human can act on.

Proposed, not run. Recording a result is a human's `ost-agent result`.

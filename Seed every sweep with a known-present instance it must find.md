---
type: Solution
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion
[[Do the shipped sweeps actually find a planted instance]]

**The idea.** Each sweep carries at least one instance it is known to be able to find, and fails if it does not find it. Not a count assertion — a positive control.

**Why it addresses what the other two cannot.** A denominator and an empty-subject guard both watch the sweep's own account of itself. A positive control checks the sweep against something outside it. Had the history sweep been required to find the known `undefined` line in the em-dashed `Daily Challenge — one shared board a day` node, it would have failed on the first run rather than printing a confident wrong number that a human then had to happen to reconcile against disk.

**The general form:** the value of a check is bounded by whether it has ever been observed failing. Every rule this project has shipped that was verified-failing-first held up; the one that was not (the lane reader) shipped with two defects.

**Where it fails.** A control chosen from the same source the sweep reads can be blind in the same way — the control has to be established independently, and keeping such fixtures current is real maintenance nobody has budgeted.

⚠️ Unvalidated. Agent-ideated from an observed failure.

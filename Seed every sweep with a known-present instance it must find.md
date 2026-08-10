---
type: Solution
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion
[[A positive control would actually fire on the sweeps that shipped]]
[[A positive control fails loudly when its plant is the wrong shape, not silently as a sweep miss]]

**The idea.** Each sweep carries at least one instance it is known to be able to find, and fails if it does not find it. Not a count assertion — a positive control.

**Why it addresses what the other two cannot.** A denominator and an empty-subject guard both watch the sweep's own account of itself. A positive control checks the sweep against something outside it. Had the history sweep been required to find the known `undefined` line in the em-dashed `Daily Challenge — one shared board a day` node, it would have failed on the first run rather than printing a confident wrong number that a human then had to happen to reconcile against disk.

**The general form:** the value of a check is bounded by whether it has ever been observed failing. Every rule this project has shipped that was verified-failing-first held up; the one that was not (the lane reader) shipped with two defects.

**Where it fails.** A control chosen from the same source the sweep reads can be blind in the same way — the control has to be established independently, and keeping such fixtures current is real maintenance nobody has budgeted.

⚠️ Unvalidated. Agent-ideated from an observed failure.

## The threshold that gated it has now been run — 2026-07-27

"Do the shipped sweeps actually find a planted instance" ran on the twelfth firing:
**12 plants, 12 found, 0 checks blind.** Its pre-commitment named this outcome explicitly —
0 or 1 means the existing verify-failing-first discipline is mostly working and this node is
"a belt-and-braces addition that can wait."

So this stays **not the primary fix**, by the test's own prior words rather than by a later
judgement call.

**But one finding argues for a narrower version of it.** All three apparent misses in that
run were defects in the *plants*, not the checks. The blindness risk that actually
materialised was in the **instrument**, not the subject — a positive control whose plant is
not the shape the check looks for reports a false alarm just as confidently as a real one.
A seeded known-present instance protects against a check going blind; it does nothing about a
seed that was never the right shape. Whatever eventually gets built here should carry an
assertion that the baseline is clean *and* that the plant is the shape the rule matches.

Annotation only — no change proposed, and the standing do-not-build is untouched.

## History
- 2026-08-05 unlinked "Do the shipped sweeps actually find a planted instance" — moved under "A positive control would actually fire on the sweeps that shipped" — the belief this test measures now has a node of its own

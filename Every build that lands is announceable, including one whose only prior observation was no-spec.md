---
type: Assumption
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility belief, surfaced beside the habituation one rather than in place of it.

The candidate assumes the event it announces is available at the moment of observation. Half of that is already true in committed code and worth recording as such: `verifyInstrument` in `src/ost/instrument.ts` returns `transitioned: true` exactly when a run comes back green on a test that was `alreadyRed`. So the flip is detected today; nothing routes it anywhere. That is a smaller build than this node's prose implies.

The other half is where this could be false, and it is specific. `observedRed` matches only log lines containing `**red**`. A vacuous run files `**no-spec**`, which that pattern deliberately does not match — that exclusion is what stops a missing file minting a build permit. The consequence for *this* candidate is the opposite of the one it was designed for: a test whose only prior observation was `no-spec` goes green with `alreadyRed === false`, so `transitioned` is false and **the announcement never fires for it**.

That is not an edge case on this tree. This vault's own measurement of 2026-08-09 found 260 of 266 recorded reds read "No test files found", and every instrument this pass could write is necessarily of that kind (see the note appended to "A pass that cannot see the repository cannot set an instrument at all"). Announcing on `transitioned` alone would therefore be silent for very nearly every build this loop actually completes — a channel that reports nothing and looks healthy.

Stated so it could be false: the moment a solution is built is detectable for every solution, not only for those whose permit rested on a spec that existed.

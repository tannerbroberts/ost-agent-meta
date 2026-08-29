---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.**

Stated so it could be false. `renderWaitShim` in `src/loop/wait.ts` ends `exit "$rc"` — the condition's own status — and at least one caller already depends on exactly that: `test/loop/wait-primitive-affordance.test.ts` asserts that a never-true condition exits with the condition's status, with `run(["exit 3", "1", "2"])` expecting `3`. Reserving a status for expiry changes a contract something reads.

The belief is that the change can be made such that expiry is distinguishable from condition-false while every *other* status the shim can return keeps its current meaning — that the only expectation that has to move is the one about expiry itself, and no caller branching on a condition's own status is silently rerouted.

It could be false in two ways worth naming: the shim may have no way to distinguish "the loop ran out of attempts" from "the last attempt returned non-zero" without an extra variable the POSIX-`sh` constraint makes awkward; and a condition that itself exits with the reserved status would become indistinguishable from expiry, re-creating the ambiguity one level down.

**What a green here does NOT settle:** whether a caller would ever read the distinction, or whether the give-up line's extra output (attempts, elapsed, output-changed) is information anyone acts on. That is usability and desirability, and no exit code answers it.

---
type: Solution
source: 'TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129'
created: '2026-08-04'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Build an index of what the project exports and what its types carry, and put it in front of the run as context rather than making it discoverable only by compiling. The `TS2552` capture is the argument: the compiler already knew `reconcileWithGit` existed and `reconcileWithUsage` did not, and it volunteered the correction. That knowledge is derivable from the same source files at any time, including before the edit.

**Shape.** A generated manifest — exported names per module, members per exported type, mutability where it is load-bearing — refreshed when source changes. Read-only; it advises, it never blocks a write.

**Against the alternatives beneath this opportunity.** This is the cheapest to build and the weakest guarantee: it makes the right name *available*, and a run can still ignore it. Edit-time checking is the opposite trade — costs a check on every write and actually refuses the mistake. Declared-intent is narrower than both: it only helps when the run knows it is calling something it has not written yet, which is exactly the `configProblem` case and not the `reconcileWithUsage` one.

**Where it plausibly fails.** A manifest for a repository this size may be too large to keep in context, in which case it has to become a lookup rather than a briefing — and a lookup the run must remember to call is a lookup the run will skip, which is the same failure this need already describes one level down.

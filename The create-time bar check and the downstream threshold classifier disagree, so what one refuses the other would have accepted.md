---
type: Assumption
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** the write-time guard in `ost_create_node` and the classifier the downstream census uses are reading the same threshold string and reaching opposite verdicts — the guard refuses a bar the census would have counted as fixed. If that is true, the guard is a false positive and this solution's premise holds. If the two agree, the guard is catching real no-bar tests and dropping it would let them through, which refutes the solution rather than costing it a guard.

**Why this is worth writing down separately from the operator's risk call.** The solution's only other assumption ("The operator will accept a no-bar test entering the tree at write time if the census still catches it") is correctly a person's answer, and it is the question that decides whether to ship. But it is asked on a premise nobody has checked: *that the guard is wrong*. An operator asked "may I relax a guard that is producing false refusals?" and an operator asked "may I relax a guard that is working?" are being asked two different questions. This belief is the one that decides which.

**What the repository already suggests, read this pass.** `A_BOUND` in `src/eval/coverage.ts` matches word-bars — `at least`, `at most`, `exactly`, `majority`, `no fewer than` — with no digit required, and `thresholdKindOf` reads a word bar as `bound`. Meanwhile the parent solution's founding observation, recorded on 2026-08-20, is that `ost_create_node` refused a no-spec instrument whose threshold spelled its numbers out and accepted the identical threshold with digits. Those two behaviours cannot both be right about the same string, which is why this reads as a live disagreement rather than a hunch — but it is read off the regexes, not observed, so it is a belief and not a finding.

**Category:** feasibility. It says nothing about whether anyone wants the guard relaxed.

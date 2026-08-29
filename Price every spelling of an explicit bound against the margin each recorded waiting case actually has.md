---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: >-
  at least 1 spelling costs no more than the blocked form on all 3 recorded
  waiting cases
instrument: npx vitest run test/loop/wait-bound-affordance-cost.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Arithmetic over strings already in the repository — no person, no interview.

**The assertion the builder has to write.** For each candidate spelling of a bounded wait, build the call the way `permittedCall` already does, price it with `expressionCost`, and compare against `expressionCost(blockedCall(c))` for all three entries of `WAITING_CASES`. The suite already has every piece: `expressionCost`, `blockedCall`, `permittedWait`, `probeOf`, and a pinned `expect(margins).toEqual([14, 25, 3])` that says exactly how much headroom each case has.

**Spellings the test must price, so it cannot pass by trying only the easy one.** The two-positional form (` 5 400`, six characters, which should fail on `condition`); a single trailing number read as the bound; a suffix on the condition string; and the bare form as the control, which must still come in at the pinned margins or the comparison has drifted. A test that priced only one spelling would report failure as impossibility, which is a different claim.

**Why it is red today.** `permittedWait(probe)` in `src/loop/wait.ts` takes one argument and emits `await '<probe>'`. There is no bounded form to price, so the function the assertion needs does not exist. Green requires a bounded spelling to exist in the module and to fit.

**Honest label on the red: `no-spec`, the weak kind.** `test/loop/wait-bound-affordance-cost.test.ts` does not exist, so today's failure is the one any question written on that path would give. This pass may not write code, and instruments are validated as argv with no shell so a name filter against the existing spec file was refused. What the builder gets instead of a blank file: the exact helpers to call, the four spellings to price, the pinned margin array to compare against, and the case (`condition`, margin 3) that decides the answer.

**What a green run does NOT settle.** Only that a short spelling exists. Whether a composer shown a bound sets a sensible one, or sets it at all, is a question about people that no character count reaches — and it is the question the parent candidate actually bets on.

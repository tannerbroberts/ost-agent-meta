---
type: AssumptionTest
created: '2026-08-22'
evidence: assertion
threshold: >-
  exactly one of three recorded-red candidates is selected, zero model passes
  are entered for the other two, and each drop names its reason
instrument: npx vitest run test/loop/confirm-before-spend.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Whether a spend happens given a state is settled by driving the selection path against fixtures; nobody's judgement is involved.

**Design.** Three candidates, each with a `**red**` recorded against its current instrument, and each in a different present state when selection runs:

| State now | Expected |
|---|---|
| the command still fails | selected; the spend proceeds |
| the command now passes (built since the observation) | dropped, and the drop reports that the permit is spent |
| the command collects no spec and the test states no bound bar | dropped, per `confirmPermit`'s existing rule |

Assert that the model pass is not entered for rows two and three, and that the reason is reported rather than the candidate silently vanishing — a loop that drops candidates quietly is indistinguishable from one with nothing to build, which is the report failure this same script has already shipped once.

**Pre-committed threshold:** exactly one of the three candidates is selected, zero model passes are entered for the other two, and each drop names its reason.

**Why it is red today, and the bound on that claim.** `buildPermit` is pure and never runs the command; `confirmPermit` exists to close that and is documented as opt-in. No `confirm` invocation appears in the portion of `build-pass.sh` read on 2026-08-22 (start through the no-build-candidates report branch), so the wiring is believed absent — but the tail was truncated by the reader's cap, so this spec settles the question rather than assuming it. If the wiring turns out to be present, the spec goes green immediately and that is itself the answer.

**What this does not settle.** Nothing about whether re-running instruments at selection time is affordable. Each confirmation spawns the repo's test runner, and the script already caps verification at eight per firing for exactly that reason — so a green here could be bought at a wall-clock cost nobody has measured. It also says nothing about the sibling reading (a missing status filter), which stands or falls on its own.

## Instrument Log
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/confirm-before-spend.test.ts` — test/loop/confirm-before-spend.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/confirm-before-spend.test.ts` — test/loop/confirm-before-spend.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/confirm-before-spend.test.ts` — test/loop/confirm-before-spend.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/confirm-before-spend.test.ts` — test/loop/confirm-before-spend.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/confirm-before-spend.test.ts` — test/loop/confirm-before-spend.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/confirm-before-spend.test.ts` — test/loop/confirm-before-spend.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/confirm-before-spend.test.ts` — test/loop/confirm-before-spend.test.ts does not exist — no spec was collected, so nothing was measured

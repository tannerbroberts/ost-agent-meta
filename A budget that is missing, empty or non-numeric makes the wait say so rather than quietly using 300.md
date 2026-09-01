---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: >-
  zero of the 4 probed environments fall back to the constant without saying so
  on stderr
instrument: npx vitest run test/loop/wait-budget-inheritance.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Executes the rendered shim under four environments — no person needed.

**The four environments, and why all four.** Budget exported and numeric (the wait must use it, not 300); budget absent; budget empty; budget non-numeric. The last three are the silent-fallback cases and each must produce a line on stderr naming the bound actually in force. Dropping any one of them makes the test passable by the cheap implementation this assumption exists to rule out — `${AWAIT_LIMIT:-300}` handles absent and empty identically and silently, and non-numeric is the case most likely to be missed because POSIX `sh` arithmetic on a non-numeric value does not reliably error and a bound evaluating to zero reads as the condition being instantly false.

**How to run it, using machinery the suite already has.** `test/loop/wait-primitive-affordance.test.ts` already writes `renderWaitShim()` into a temp dir at mode `0o755` and executes it through `execFileSync("sh", [bin, ...args])`. The same helper with an `env` override gives all four environments. Assert on the stderr line and on the observed give-up time, not on the source text — a test that greps the rendered script for a variable name would pass on a shim that reads the budget and then ignores it.

**Why it is red today.** `renderWaitShim()` emits `limit=${3:-300}` and reads no environment at all, so there is nothing to inherit and nothing to announce. Green requires both halves: the inheritance and the announcement.

**Honest label on the red: `no-spec`, the weak kind.** The named file does not exist, so it fails for a reason not specific to this question. The stronger form — an assertion filter against the existing spec — is not expressible, because instruments are argv-only and quoted `-t` filters are refused. The paragraphs above are what stand in for it.

**What a green run does NOT settle.** Whether the budget can be plumbed from the harness into the wrapper's environment in the first place; that is a question about what a firing's wrapper can see, and this test assumes the export exists in order to probe what happens when it does not. It also says nothing about whether the composer's own number is a good one.

## Instrument Log
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/loop/wait-budget-inheritance.test.ts` — test/loop/wait-budget-inheritance.test.ts does not exist — no spec was collected, so nothing was measured

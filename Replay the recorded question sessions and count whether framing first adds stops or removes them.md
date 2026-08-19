---
type: AssumptionTest
source: 'agent-ideated:2026-08-04-unattended-sweep-question-shape'
created: '2026-08-04'
evidence: assertion
threshold: >-
  Across every recorded session carrying a clarifying_question, the two-stage
  form produces no more total operator turns than the one-stage form did.
instrument: npx vitest run test/loop/two-stage-question-stop-count.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Feasibility, and the arithmetic the solution depends on.** Framing first is only worth it if questions are rejected often enough that the saved three-turn failures outweigh the added second turn on every accepted question. That base rate is unmeasured, and the harvested transcripts already hold it: every `clarifying_question` event with its outcome — accepted, or `permission_denied` and re-asked.

Count the total operator turns the recorded sessions actually cost, then count what the two-stage form would have cost on the same material, and compare. No new sessions, no recruiting.

**Lane: compute-only.**

**What this does not settle.** This is a replay against history, so it answers whether the trade would have paid off on questions this run has already asked. It cannot tell you whether framing first makes the operator's answers *better* — a shorter exchange that reaches the wrong decision is worse than a long one — and it cannot speak for question shapes that have not occurred yet.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — test/loop/two-stage-question-stop-count.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — test/loop/two-stage-question-stop-count.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 16ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 5ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-13 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 19ms
- 2026-08-14 **red** (exit none) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — spawnSync npx ETIMEDOUT
- 2026-08-14 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 5ms
- 2026-08-14 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-14 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-14 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 15ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 18ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 18ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 21ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-15 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-16 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-16 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-16 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-16 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — test/loop/two-stage-question-stop-count.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms
- 2026-08-19 **red** (exit 1) `npx vitest run test/loop/two-stage-question-stop-count.test.ts` — ❯ test/loop/two-stage-question-stop-count.test.ts (6 tests | 1 failed) 4ms

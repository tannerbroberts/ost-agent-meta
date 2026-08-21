---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  2 of 2 recorded branch↔solution pairs (run-tool-surface → "Every run records
  the tool surface it actually had"; two-stage-question-stop-count → "Ask the
  open question first, and offer options only once the frame is agreed") resolve
  to their own title with coverage ≥ 0.6 and margin ≥ 0.15, and 0 resolve to any
  other buildable title
instrument: npx vitest run test/loop/branch-name-resolves-target.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec asserts.** Build a briefing document from the buildable titles recorded for the firings that produced PR #181 and PR #130, feed each recorded branch name to `resolveWorkItem` from `src/loop/claim.ts` (the matcher the solution proposes to reuse, with its defaults `DEFAULT_MIN_COVERAGE = 0.6` and `DEFAULT_MIN_MARGIN = 0.15`), and assert that each resolves to its own solution and that neither resolves to a different title.

**Lane: compute-only.**

**Why it is red today, and what kind of red.** `test/loop/branch-name-resolves-target.test.ts` does not exist — this is a **no-spec red**, declared as such, and it mints no permit until the spec is written and an assertion in it fails. The assertion is expected to fail genuinely once written: `two-stage-question-stop-count` shares one significant term with its solution's title, which claim.ts's own header predicts is under the bar. If it passes on the first run, the assumption holds more strongly than its author expected and the instrument should be re-pointed at a harder recorded pair rather than loosened.

**What a green does NOT settle.** That the matcher works on these two pairs says nothing about a convention-free future branch name, nothing about whether the operator wants selection consulting the forge at all, and nothing about the stranding risk of an abandoned open branch. Feasibility of resolution only.

## Instrument Log
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/branch-name-resolves-target.test.ts` — test/loop/branch-name-resolves-target.test.ts does not exist — no spec was collected, so nothing was measured

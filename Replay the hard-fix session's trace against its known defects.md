---
type: AssumptionTest
status: unvalidated
source: >-
  founder-directive:2026-07-24 — assertion-vs-trace distinction, stated in
  session
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/telemetry/trace-defect-replay.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (desirability):** a counts-and-timings rollup carries decision-changing signal, not just activity decoration.

**Method:** the 2026-07-24 hard-fix session left ~50 tool invocations and two independently-confirmed defects (serializer strips `evidence:` frontmatter on rewrite; `ost_create_node`@0.1.3 silently drops the `evidence` input). Hand the day's trace rollup to a reviewer who does not know the defects and ask what looks wrong. One sitting, existing data.

**Pre-committed threshold:** the rollup alone surfaces >= 1 of the 2 known defects. At 0, the statistics are decoration and the solution needs vault-diff awareness added or dies in favor of the reconciler sibling.

**Decides:** whether the shipped rollup stays as-is, grows diff-awareness, or yields to the reconciler.

*Proposed by the agent — to be run by a human. No results recorded here.*

## History
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/trace-defect-replay.test.ts — Replays the hard-fix session's trace and asserts each known defect is visible in it, which is what a trace has to do to be worth keeping; fails today because the rollup discards the detail the defects show up in.

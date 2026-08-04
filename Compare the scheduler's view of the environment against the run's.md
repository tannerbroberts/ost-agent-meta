---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  10 consecutive dispatches agree exactly between the scheduler's preflight and
  the run's own reading. One disagreement fails it.
instrument: npx vitest run test/loop/preflight-parity.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** A preflight is only worth anything if the scheduler sees what the run will get. If it checks from a different shell, user, or working directory, a green preflight proves nothing — and this vault has already paid for that exact divergence once, in the evidence behind [[A recorded failure can't be reproduced, because the record omits where it ran]], where a step failed purely because it ran from the wrong directory.

**The test.** Have the scheduler record its reading of the environment at dispatch; have the run record its own reading in its first second; compare the pairs over ten consecutive dispatches. Compare the whole picture, not just tool presence — working directory, resolved `PATH`, user, and vault reachability — because those are the axes that diverged before.

**Why one disagreement fails it.** The claim being tested is *the preflight is authoritative*. A preflight that is usually right is not a preflight, it is a hint, and a hint that prevents dispatch will eventually cancel a run that would have worked. Ten clean pairs is a modest bar and the failure mode is asymmetric enough to justify a strict one.

**Why it is cheap.** Both readings are already being taken if [[Declare the tool surface a pass requires and abort in the first second if it is absent]] ships; this test is the comparison, not new instrumentation. Running the two candidates in that order costs almost nothing extra and answers both questions.

**What a failure would tell you.** Not that the scheduler is useless — that the check must run *inside* the dispatched context rather than in the scheduler's, which is a different and still-valuable design.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/preflight-parity.test.ts — Captures the scheduler's environment reading at dispatch and the run's own reading in its first second — working directory, resolved PATH, user, vault reachability — and asserts all ten consecutive pairs agree exactly, the node's strict bar. It fails today because neither reading is taken anywhere, so there is nothing to compare.

---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-02-maintenance-pass-3'
created: '2026-08-02'
evidence: assertion
threshold: >-
  At least 3 of the 5 replayed blockers nameable as a resource at least one pass
  before the pass that stalled on them; 2 or fewer kills it as a planner input.
instrument: npx vitest run test/loop/blocker-mining-replay.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that the stalls this loop already records carry enough structure for a mechanical scan to name the underlying *resource* — not just the error — and to name it early enough to redirect the next pass rather than only to explain the last one.

**The test:** take five constraints this vault discovered the expensive way and whose history is fully written down — the unpublishable release, the refused tag push, the absent human hours, the declined cold outreach, and the five scheduled passes that ran with no `ost_*` tools. For each, find the earliest artifact in the vault or the friction channel that a scan could have read, and check whether that artifact names a resource rather than only an error string. Then count how many were nameable at least one pass before the pass that stalled on them.

**Pre-committed before running:** three of the five must be nameable one pass early. Two or fewer kills the candidate as a planner input — it would still be a useful post-mortem, but it could not claim to prevent anything, and this opportunity is about planning rather than reporting.

**What it deliberately does not cover:** abundance. No stall exists for a resource the project has plenty of, so this test cannot say anything about the founder's own strongest example — capital with a deadline — and a passing result must not be read as covering it.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/blocker-mining-replay.test.ts — Mines the recorded run history up to each known blocker and asserts the constraint profile names it before the pass that hit it; fails today because nothing mines blockers into a profile.

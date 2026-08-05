---
type: AssumptionTest
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: assertion
threshold: >-
  At least 3 distinct test files were hand-excluded across the captured
  sessions; at one or two, a committed list is over-engineering.
instrument: npx vitest run test/telemetry/hand-exclusion-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.**

The assumption is that there is enough of this to be worth a mechanism. A committed quarantine list is infrastructure — a file format, a runner change, a review habit — and if the entire observed history is one flaky file excluded by one person, the honest answer is to fix that file and build nothing.

**Design.** Scan every captured session's shell invocations for exclusion flags and filters, extract the test paths, and count the distinct set. Also count how many separate sessions each appears in, since one file excluded across many sessions argues for expiry rather than for a list.

**Why it is small.** The invocations are already harvested; this is extraction and counting.

**Why the threshold is set where it is.** Below three distinct files this candidate loses to simply fixing the flake, and that is a result worth being able to get — a test that cannot come out against its own candidate is not doing anything. The current record is known to contain at least one file (`test/mcp/wall-clock-budget.test.ts`, excluded three times in one session on 2026-08-04), so a red here is a live possibility rather than a formality.

**What it will not cover.** It cannot see exclusions that were never typed because the operator gave up and ran a narrower suite instead, and it says nothing about this candidate's real hazard — that a comfortable quarantine lowers the cost of never fixing anything, which is why [[Quarantine entries expire, so a workaround cannot become permanent by inattention]] may be a precondition rather than a sibling.

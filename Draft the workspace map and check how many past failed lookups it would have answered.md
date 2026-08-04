---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  A map under 2,000 characters answers at least 70% of the observed failed
  lookups.
instrument: npx vitest run test/runner/workspace-map-coverage.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a map small enough to carry is large enough to help. One big enough to answer every question is too large; one small enough will omit the thing being looked for often enough that the probing habit persists, and the failed probes then cost the same as before plus the map.

**Risk category: feasibility.**

**Design.** Draft the map at a stated size — say two thousand characters. Take every failed path lookup in the harvested transcripts and check, one by one, whether the map would have supplied the answer. Then try a map at half the size and one at double, and plot coverage against size.

**Why it is small.** The failed lookups are already captured, and drafting three maps is minutes.

**What it will not cover.** It tests the map against paths that were actually reached for, which were shaped by not having one. It also says nothing about staleness during long runs.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/workspace-map-coverage.test.ts — The threshold — "a map under 2,000 characters answers at least 70% of the observed failed lookups" — is settled entirely against committed state: the spec renders the workspace map, asserts its serialized length is under the stated budget, replays every failed path lookup in the harvested transcript corpus against it, and asserts the answered share clears 70%. It fails today because nothing in the repository renders a workspace map at all.

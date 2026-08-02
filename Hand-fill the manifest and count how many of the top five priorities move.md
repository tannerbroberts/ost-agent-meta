---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-02-maintenance-pass-3'
created: '2026-08-02'
evidence: assertion
threshold: >-
  At least 2 of the current top 5 priority positions change, or an item
  enters/leaves the top 5; 1 or 0 changes kills the candidate.
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (desirability / value):** that a declared resource picture actually changes which work comes first. If the ranking is identical with and without it, the manifest is documentation, not a planner input, and should not be built.

**The test:** fill the manifest by hand for this vault from facts already recorded in it — zero human hours, no willingness to cold-contact strangers, no publish credential reachable from the container, a token budget with a reset schedule, no capital. Re-derive the top five items of the current priority order under those declared constraints, without looking at the existing order while deriving. Then diff the two lists.

**Pre-committed before running, so this can come out a failure:** two of the current top five must change position, or an item must enter or leave the top five. One change or none kills the candidate — it would mean the planner was already conditioning on these facts implicitly and the manifest buys nothing.

**What it deliberately does not cover:** whether an operator who is *not* the founder would fill the manifest at all, and whether the answers stay true. Those are the questions [[Expiring resource questions asked at a fixed cadence]] carries.

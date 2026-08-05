---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Ordering by time-to-kill eliminates more candidates per hour than ordering by importance]]

Order the test queue not by importance but by expected time-to-kill: run first whatever could eliminate the most candidates for the least effort. Optimises for shrinking the consideration set quickly rather than for building confidence in a favourite.

**Contrast with siblings:** Directly inverts the usual instinct to test the most promising idea first. Needs a stock of candidates and tests to be worth anything, so it composes with (rather than replaces) "kill criteria"; unlike the tournament it never compares candidates to each other.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Does cheapest-disconfirmer ordering eliminate more candidates per hour spent]] — moved under [[Ordering by time-to-kill eliminates more candidates per hour than ordering by importance]] — the belief this test measures now has a node of its own

## Definition of done

[[Does cheapest-disconfirmer ordering eliminate more candidates per hour spent]]

`npx vitest run test/ost/disconfirmer-ordering.test.ts`

The spec asserts the inversion the node is built on: the queue orders by expected candidates-eliminated-per-effort rather than by importance, and a fixture where the two orderings disagree comes out in the disconfirmer order. Red today because the queue has no ordering beyond the lane it sorts by.

**What a green here does not settle.** Whether the ordering actually eliminates more per hour — that needs tests to have been *run*, and this tree has recorded zero results across 255 tests, so the measurement the threshold asks for is not currently obtainable at all. That dependency is worth naming: this node cannot be evaluated until something in [[Tests get written and instrumented all day, and not one of them has ever been run]] gets built. Nor can a spec estimate time-to-kill honestly; it can only check that whatever estimate was supplied was the thing sorted on.

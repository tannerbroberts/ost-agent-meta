---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An operator shown the evidence will accept an elimination they initially disagreed with]]

Run candidates against each other in rounds — each round eliminates on a specific piece of grounded evidence rather than crowning anything. Matches the ruleset's own position that "good" is only judgeable relative to alternatives, and produces a shrinking consideration set without ever declaring a winner (which remains a human decision).

**Contrast with siblings:** The only option that yields a *relative* judgement, so it works when no candidate has absolute evidence — and the only one that can be run on the existing untested tree today. Costs the most reasoning per round, and a bad bracket can eliminate a good candidate early.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Would an operator accept an elimination they initially disagreed with once shown the evidence]] — moved under [[An operator shown the evidence will accept an elimination they initially disagreed with]] — the belief this test measures now has a node of its own

## Definition of done

[[Would an operator accept an elimination they initially disagreed with once shown the evidence]]

`npx vitest run test/eval/tournament-elimination.test.ts`

The spec asserts the two properties that make this a tournament rather than a ranking dressed up: every elimination cites a specific evidence id or recorded result, and no round ever crowns anything — the consideration set only shrinks, and declaring a winner stays a human's call. Red today because no tournament exists and nothing enforces that an elimination be grounded.

**What a green here does not settle.** Whether an operator accepts an elimination they disagreed with, which is the actual test and needs a person. Also untouched is the node's own stated weakness: a bad bracket can eliminate a good candidate early, and a spec that checks every elimination was *grounded* cannot check the bracket was *fair*. Worth reading the provenance caveat above alongside this — the whole idea is founder-stated in a single spoken rant, resting on the `assertion` floor, and a runnable command does not move it up the ladder by one rung.

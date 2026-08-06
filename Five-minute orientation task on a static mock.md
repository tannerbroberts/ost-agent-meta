---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
---
#AssumptionTest #unvalidated #usability #evidence/assertion

**Assumption under test (usability, with desirability implications):** A rendered tree lets someone who has never seen it answer "where are we, and what is weakest?" unaided — and that structure is what they wanted rather than a plain verdict.

**Proposed test:** Build a static mock of the current tree. Give five people two tasks: "tell me what changed since last week" and "tell me which part of this is least trustworthy." Watch silently. Afterwards ask what they would have preferred to see instead.

**Size:** one mock image and five ten-minute sessions; no working software.

**Pre-committed threshold:** ≥3 of 5 answer both tasks correctly within 3 minutes each, with no hints. Track the "what would you have preferred" answers — if most name a written summary, the sibling digest wins regardless of this score.

Proposed by the agent — to be run by a human with real observers. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-05 2026-08-05 unattended sweep — triaged as humans-required, lane not settable from this surface. Its parent solution "Rendered tree view with diff since last visit" sits in `solutionsMissingInstruments`, and no instrument belongs here: the measurement is strangers being observed — "Give five people two tasks ... Watch silently", "to be run by a human with real observers" — with a threshold (≥3 of 5 answer both tasks correctly within 3 minutes, unaided) that only exists relative to real observers. `ost_flag_humans_required` was refused on this sweep (not granted), so a human should set the lane with `ost-agent lane --set`. Recorded so this is not re-triaged next pass.
- 2026-08-06 2026-08-06 Reached via `solutionsMissingInstruments` for "Rendered tree view with diff since last visit"; deliberately left without an instrument. This test measures whether a person orients faster from a rendered tree than from the files — comprehension by a reader who is not the author. No spec file can settle that: a passing test could only assert that the renderer emits the shapes it was told to emit, which is a restatement of the implementation and not the question. The right label is humans-required, and this pass could not apply it — `ost_flag_humans_required` is withheld on this unattended surface, and the permissive direction is a human's `ost-agent lane --set` in any case. For a human: label this humans-required so it stops appearing as un-instrumented debt, and note that it can be run against a static mock before anything is built, which makes it unusually cheap for a desirability test.

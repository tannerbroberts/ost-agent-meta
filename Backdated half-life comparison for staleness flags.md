---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
authorship: machine
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** A decay rate exists that flags genuinely stale nodes without crying wolf on needs that are simply stable.

**Proposed test:** Have a human mark, by hand, which nodes in a backdated sample they consider stale. Then apply three candidate half-lives — say one month, three months, a year — and compare each setting's flags against the human's list.

**Size:** an offline calculation over existing nodes plus one review session.

**Pre-committed threshold:** at least one setting catches ≥80% of the human-marked stale nodes with ≤1 false flag. If no setting clears both, staleness is not a function of time here and the mechanism should be evidence-triggered instead.

**Decides:** whether decay can be automatic, and at what rate.

Proposed by the agent — the human's stale list must be produced before seeing any setting's output. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-29 2026-08-29 unattended sweep: this test is humans-required in substance but carries no `lane:` field, so it counts in the 68 unlabelled tests rather than the 54 labelled ones, and its parent solution is reported as missing an instrument every pass. Its own design is why no command can settle it: the human must mark, by hand, which nodes they consider stale BEFORE any half-life setting's output is shown to them — a blind human list is the measurement, and generating it with compute would be the graded party grading itself. An instrument here could only ever compute the three candidate settings' flags, which is the half that was never in doubt. Not labelled by this pass because `ost_flag_humans_required` is withheld on the unattended surface; the move is `ost-agent lane --set` and is the operator's. Recorded on the node so the next pass reads it here instead of re-deriving it. Full census context on "The biggest queue on my report is one the surface reading it to me has no tool to clear".

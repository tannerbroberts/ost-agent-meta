---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (desirability):** an unblock-count ranking changes which node the operator picks up — otherwise it is decoration.

**Method:** the human operator picks a next build naively from each live vault; then is shown hand-computed unblock counts; record whether the pick changes and whether the operator judges the change an improvement. About an hour. Guard: the OPERATOR is the subject — an agent picking would re-create the closed loop this tree already flags.

**Pre-committed threshold:** the pick changes and is judged an improvement in >= 1 of 2 vault trials, else the ranking is not built.

**Decides:** unblock-ranking vs prerequisite edges vs the route view — three computed-ordering siblings, one winner.

*Proposed by the agent-side hard-fix pass — to be run by a human. No results recorded here.*

## History
- 2026-07-24 evidence: (none) → assertion — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input

## Issues
- 2026-08-05 2026-08-05 unattended sweep — triaged as humans-required, but the lane could NOT be set, so this is a note rather than a label. Its parent solution "Rank every node by how many blocked tests one build would unblock" sits in `solutionsMissingInstruments`, and this pass judged that no instrument belongs here: the method makes a person the measurement and says so as an explicit guard — "the human operator picks a next build naively from each live vault; then is shown hand-computed unblock counts", with "Guard: the OPERATOR is the subject — an agent picking would re-create the closed loop this tree already flags." No spec file can supply an operator's changed pick. The correct disposition is the humans-required lane; `ost_flag_humans_required` is not on this unattended sweep's granted surface (the call was refused), so a human should apply it with `ost-agent lane --set`. Recorded here so the next pass reads the disposition instead of re-deriving it from the test body.

---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
evidence: assertion
authorship: machine
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
- 2026-08-06 Lane finding, unlabelled because the label was refused. This test is humans-required and says so in its own guard: "the OPERATOR is the subject — an agent picking would re-create the closed loop this tree already flags." The measurement is whether a person's choice of next build changes when shown the ranking, which no exit code reports. This pass attempted `ost_flag_humans_required` and was denied the tool, so the frontmatter carries no `lane:`. A human should set it with `ost-agent lane`.

Note the split this implies for the parent solution "Rank every node by how many blocked tests one build would unblock": computing the unblock count is entirely mechanical and could carry its own instrumented test, while whether the count changes anybody's pick cannot. The solution currently rests only on the human half, so it has no runnable definition of done at all — which is why it appears in `solutionsMissingInstruments` even though half of it is trivially testable.
- 2026-09-02 2026-09-02 unattended sweep, repo sight held — the closing paragraph of the 2026-08-06 note above has gone stale and should not be acted on. It reads: "The solution currently rests only on the human half, so it has no runnable definition of done at all — which is why it appears in solutionsMissingInstruments even though half of it is trivially testable." That was true when written and is not true now. The parent solution "Rank every node by how many blocked tests one build would unblock" was read in full this pass and carries a Definition of done naming a command, `npx vitest run test/rank/unblock-leverage-distribution.test.ts`, hung on its sibling assumption "Unblock counts are near-uniform across a real tree, so ranking by them orders nothing" — which is exactly the mechanical half that paragraph says is missing: it computes the unblock-count distribution over this vault and requires it to be non-flat, with green meaning the top-ranked build unblocks at least 3x the median and the top decile carries at least a quarter of all unblockings. So the split this note correctly identified has since been built, by giving the computable half its own assumption and test rather than by loading a second lane onto this one. What is unchanged, and is why this note is corrected rather than withdrawn: THIS test is still humans-required and still unlabelled. Its own guard is decisive — "the OPERATOR is the subject — an agent picking would re-create the closed loop this tree already flags" — and no exit code supplies an operator's changed pick. The repair remains one command, `ost-agent lane --set`, because ost_flag_humans_required is withheld from the unattended surface. Recorded because this test was read as one of the two riskiest members of the 46 people-shaped entries classified by title alone on "The biggest queue on my report is one the surface reading it to me has no tool to clear" — the check confirmed the classification and turned up this stale claim alongside it. Nothing was executed, no lane set, no instrument set, no rung moved.

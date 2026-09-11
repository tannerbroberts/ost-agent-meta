---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Two failures being the same class is decidable by a rule that matches hand grouping]]

The tool surface keeps a small in-session tally of refusals by class. The first occurrence is answered as it is now. The second escalates: it leads with the fact that this is a repeat, quotes what was said the first time, and states plainly that the previous correction was not applied. A third stops being advice and becomes a refusal to proceed on that route until something changes.

The change is entirely in the framing. A message that reads as a fact about one command invites retry; one that reads as a fact about the last three minutes does not.

**Compared to the alternatives.** This is the only option that acts inside a single session, which is where the sharpest evidence sits — five identical shell errors in one transcript, eleven sessions each rediscovering the same blocked-sleep refusal from scratch. A corrections file cannot help there at all, because the lesson has nowhere to travel to. Conversely this carries nothing forward: a fresh session starts its tally at zero and repeats the first mistake exactly as before.

**What would make this the wrong pick.** It depends on classifying two failures as the same, and that is the whole difficulty. Grouping too tightly catches nothing; too loosely and it starts refusing routes that merely rhyme, which is worse than the problem.

## History
- 2026-08-05 unlinked "Group the harvested tool errors by hand and see whether one rule reproduces the grouping" — moved under "Two failures being the same class is decidable by a rule that matches hand grouping" — the belief this test measures now has a node of its own

## Issues
- 2026-09-11 2026-09-11 unattended sweep, repo sight held. First examination recorded on this node, which surfaces in solutionsMissingInstruments. Three findings for a human. (1) PLACEMENT: this hangs under "The same refusal is rediscovered every session, because nothing carries the lesson forward", but its own prose says it "carries nothing forward: a fresh session starts its tally at zero" — it is the in-session contrast candidate, not an answer to the cross-session need. (2) NEAR-DUPLICATE ACROSS BRANCHES: "The tally is kept and the second occurrence is met with the count, not the correction", under "I repeat one shell mistake five times in a session, because the first failure never said it was a class", makes the same claim (in-session class tally; second occurrence leads with the repeat and quotes the first correction). The only thing this node adds is that a third occurrence becomes a refusal to proceed on that route. Not merged: a merge repoints this node's inbound edge onto the survivor, which already has a parent, so it would create a second parent (single-parent rule). Which branch it belongs to is a restructuring call for a human, not an unattended pass. Suggested repair: merge into the sibling, folding the third-occurrence refusal in as the contribution, and remove the edge from the cross-session opportunity. (3) NO INSTRUMENT, deliberately: its only test, "Group the harvested tool errors by hand and see whether one rule reproduces the grouping", is measured against a person's hand grouping, so the labels are the measurement. The mechanical half (does a counter group a replayed session's repeats and fire by the second) is already instrumented on the sibling as `npx vitest run test/loop/repeat-class-escalation.test.ts`. Setting that same command here would give this node a second definition of done for the same spec. Nothing executed, no instrument set, no status or rung changed.

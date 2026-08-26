---
type: Solution
source: 'TRANSCRIPT:98dcaba0-5cd8-4e56-8360-55b58a655cd8'
created: '2026-08-26'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The founder will keep a manifest of prescribed call sequences current as the loop's steps change]]

**Variation dimension: automated-vs-manual. Position taken: the matching is automated, the definition of "procedure" is deliberately left manual.**

A small declarative manifest lists the call sequences that are procedure rather than pain — `ost_ingest_inbox` followed by `ost_next_work` at the close of a pass; a blocking `TaskOutput` on a task the same session started. The harvester matches every candidate friction event against it and suppresses the matches automatically, with no judgement at harvest time. What stays manual is the list itself: a person edits it, because what counts as prescribed is set by the ruleset the person writes, and the ruleset changes.

**Why the manual half is the point, not a shortcut.** The loop's procedure is not a property of the code — it lives in the skill text and the firing prompt, both of which a human rewrites. Any mechanism that infers "prescribed" from the code would be reading the wrong artifact and would go silently stale the next time the loop's steps change. Making the list an artifact a person edits keeps it in the same place as the thing it describes, and a manifest entry that no longer matches anything is visible in a way an inference is not.

**Against the siblings.** Unlike deleting the `retry` class, this keeps genuine retry-after-failure signal intact — a repeat that is not on the list still files. Unlike adopting the host's error flag, the suppression rule is authored here and can encode this product's own procedure, which no upstream signal knows anything about.

**What it costs.** A maintenance burden with a known failure mode: this project's own tree already records that artifacts asking for recurring founder input are the ones that go unmaintained, and there is a live assumption elsewhere on exactly that question ("The founder will actually maintain a highlight criteria note over time"). A stale manifest fails in the dangerous direction — it keeps suppressing a sequence that has stopped being procedure, so real friction goes missing rather than merely unfiltered.

**What would make this the wrong pick.** If the prescribed sequences turn out to be few and stable, a manifest is ceremony around two hard-coded rules. If they turn out to be many and fast-changing, nobody will keep it current. It is the right pick only in the middle case.

Unvalidated — a human to review.

## Definition of done — and it is not a command

"Count how many recurring-input artifacts the founder has actually kept current, before asking for another"

There is deliberately no instrument here. The belief this candidate rests on is whether one specific person keeps one more list current, and the bar is: at least 2 of the founder's existing recurring-input artifacts were edited within 30 days of the change they were meant to track. A script can gather the timestamps that start the conversation; it cannot supply the half that decides the answer, which is why an artifact that went stale went stale.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Sequencing this candidate against its siblings:** this is the cheapest of the three to build and the only one that can fail after it ships, silently, by suppressing a sequence that stopped being procedure. So the viability answer should come before the build, not after — and if it comes back below the bar, the sibling that deletes the repeat inference outright is the default, because it asks nobody for anything.

**Lane note for a human:** this test was created in the humans-required lane at creation time. `ost_flag_humans_required` is withheld on the unattended surface, so if the lane ever needs changing it is `ost-agent lane --set`.

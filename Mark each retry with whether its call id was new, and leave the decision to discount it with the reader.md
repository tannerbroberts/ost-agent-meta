---
type: Solution
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
killIf: >-
  Shown records that split same-id from new-id retries, the next three passes
  that read them still cite a same-id retry as friction in a node they write
killBy: '2027-04-17'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A reader shown the same-id split stops treating those retries as friction]]

**Variation dimension: automated-vs-manual. Position taken: the detecting stays automated, and the judgement is deliberately left manual.**

The harvester keeps filing every retry it files today. What it adds is one fact per event: whether the call's `tool_use` id had already been seen in the session. The record's summary line splits the count: `retry ×8 (8 reused an id already seen, 0 new calls)`. A reader, human or a later pass, decides what a same-id retry means. Nothing is dropped automatically.

**Why leave the judgement manual.** Each sibling decides on the reader's behalf that a same-id repeat is noise. That is very likely right. But the cases where it is wrong look identical in the record, and an automatic drop is the one change nobody can see afterwards. This candidate pays for visibility with a longer record and a reader who has to do the discounting.

**What it deliberately gives up.** It does not shrink the evidence queue at all. Every same-id record still arrives as unmapped evidence and still costs a reader its full length to decline. If the readers are passes like this one, which already over-read the queue, this candidate adds information to a channel that is short of attention, not of information. That is its main risk, and the test beneath it is aimed at it.

**What it does not touch.** Prescribed repeats get `new id` and look exactly like real retries, so the parent's problem is unchanged.

**Honest note on how this was ideated.** All three candidates under this opportunity were written in one context by one author, one after another. This surface cannot run independent blind ideators, so discount their apparent distinctness.

Unvalidated. Agent-ideated 2026-10-17; for a human to review.

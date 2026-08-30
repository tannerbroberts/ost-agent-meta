---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
killIf: >-
  Eight weeks after the route ships, no ask that arrived through it has been
  answered by anyone
killBy: '2026-12-31'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The operator answers an ask that arrives with a clock on it at a rate above zero]]

**Variation dimension: where-it-lives — which queue the item is reported in. Position taken: it moves, and nothing is hidden.**

Do not filter the item away. Re-file it. A Solution whose every test is in a lane compute may not run leaves `solutionsMissingInstruments` and appears in `outstandingAsks`, which this sweep already emits, already carries the pre-filled `ost-agent result` line for, and already ages by how long the ask has gone unanswered. The item keeps its visibility and changes its claim: from "you failed to write a command" to "a person owes an answer, and it has been open N days."

**Why this position and not another.** The sibling that filters says the listing was wrong; this one says the listing was in the wrong place. The information a reader actually needs here is not "does this have a command" but "who is this waiting on and for how long" — and there is already a queue that answers exactly that, with an ageing field the filter candidate throws away. This vault's `outstandingAsks` currently holds 59 entries of which 59 have no recorded age, so the ask queue's own weakness is that things arrive on it without a clock; routing gives these arrivals a start date.

**Cheapest form.** Where the lane check would go in `solutionsMissingInstruments`, emit into the pending-ask path (`src/ost/pending-asks.ts`) instead of dropping, tagged with the solution that owes it, so the ask reads as "this solution is blocked on a person" rather than as a bare test title.

**What it deliberately does not do.** It takes no view on whether the lane is right. A mislabelled test routes just as smoothly as a correctly labelled one — this candidate improves where the item is filed and not whether it deserved the label, which is the third sibling's whole subject.

**What it gives up, plainly.** It is the most expensive of the three to build and the only one that makes a queue longer. The ask list already stands at 59 unanswered, and this pours 68-ish more onto it; if the operator is not answering the 59, adding to the pile converts an unclearable instrument bucket into an unclearable ask bucket and this candidate has achieved nothing but a rename. That is a real risk and the test beneath it is aimed squarely at it. It also cannot age what has already happened: everything routed on day one gets today's date, so the ageing column starts by lying about how long these have actually been open.

**What would make this the wrong pick.** If the operator's answering rate is near zero, routing is ceremony and the filter sibling is strictly better. If the operator does answer asks but has never seen these because they were buried in the wrong queue, this is the only candidate that helps at all.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.

## Definition of done — and it is not a command

"Count how many routed asks the operator answers in the four weeks after they arrive with an age on them"

No command: this one is humans-required on purpose. The bar is **at least 5 of the routed asks answered within 4 weeks**. An exit code can prove the entries moved queues; it cannot observe whether anybody answered them, and whether they get answered is the entire belief this candidate rests on. The half that decides the verdict is why an unanswered entry went unanswered — mis-filed, too expensive, or no longer interesting — and no artifact on disk carries that reason.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

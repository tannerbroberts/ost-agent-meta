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

## Standing finding — what nine follow-up notes established (consolidated 2026-11-10)

**For a firing that meets this node in `solutionsMissingInstruments`: the cheap check comes first.** Run `ost_read_repo` with `probe: true` on `src/eval/buildable.ts`. If it still reads **23,611 bytes** and this node is still in the bucket, nothing has moved and nothing below needs re-deriving. It read 23,611 on 2026-10-11, 10-31, 11-07, 11-09 and 11-10. Add a line here only if that changes.

**1. The bucket holds owed answers, not unwritten commands.**
- The shown page of 25 was classified in full on 2026-09-03 (9 bodies read, 16 judged by title): **zero instrumentable**. Six name a harness artefact that is not in this repository (the Monitor pair, the background-task output directory, the job-control wait, harness compaction, the auto-read guard). Eighteen rest on desirability or viability. One, "Append-only tool surface with no delete or shell tool", would take a false red: a spec asserting "no delete tool" fails today only because the delete was added on purpose.
- The unlabelled, uninstrumented tests were enumerated on 2026-09-01: **67**, of which 46 name a human act in the title, and 14 of the other 21 had been examined with none instrumentable. The remaining 7 were not examined as of that note. On 2026-10-19 the stock was still 67 and none was created after 2026-08, so it is fixed legacy.
- The 45 entries beyond the shown page have never been paged to from this surface.

**2. For lane-labelled tests the routing has already happened, so the candidate is de-duplication there.** Lane-labelled tests and `outstandingAsks` were the same count on 2026-09-01 (62 and 62) and again on 2026-10-19 (69). A solution whose only test is labelled sits in both queues at once. That was checked per file on this node and on "Group the queue by error signature at read time, and change nothing on disk", not on all 70. So "instead of" in this node's title overstates the move, and the "pours 68-ish more" cost applies only to the unlabelled 67. A more accurate title would be nearer "stop counting a labelled test twice". The body was not rewritten to say so, because narrowing what a candidate proposes is the operator's call.

**3. The cause is a missing branch, read in source on 2026-09-07.** `solutionsMissingInstruments` in `src/eval/buildable.ts` (20,070 bytes at the time, read in full) excludes four things: non-Solutions, `status === "deferred"`, shipped solutions that `trustsShippedStatus` accepts, and solutions with no tests. It reads no `lane`. In the same module `testsAwaitingVerification` does: `if (n.lane === CAUTIOUS_LANE) continue;`. The repair is one line in a function that already imports the predicate. A spec for it would be an added assertion in an existing `test/eval/` suite (`clearability.test.ts`, `permit-staleness.test.ts`, `vacuous-red.test.ts`), so it would fail on the assertion and not as `no-spec`. Which file is the right home was not judged; `clearability.test.ts` is 33KB and was not read.

**4. It has not landed, and that rests on behaviour.** The file grew to 23,611 bytes by 2026-10-11 and now truncates before the function, so the body has not been re-read since 2026-09-07. What shows the branch is still missing is that this node is still listed while its only test reads `lane: humans-required`.

**5. The bucket now grows only when a pass labels a human-owed test correctly at birth.** Counts on 2026-10-19: 523 tests, 387 with `instrument:`, 69 with `lane:`, 67 with neither. The bucket went 69 (2026-08-30), 72 (2026-10-19), 70 (2026-11-10).

**6. Nothing on the unattended surface can clear it.** `ost_flag_humans_required` is withheld there. The exits are the code repair, or a human's `ost-agent lane --set` per test. Granting the label call to the unattended surface is a third route; it is a permission decision and the operator's.

**7. What re-checking has cost.** Between 2026-10-28 and 10-31, four sessions tried to Grep `src/eval/buildable.ts` directly and were refused on repo permission, and a fifth tried to read `test/eval/lane-aware-instrument-bucket.test.ts`, which does not exist. Five consecutive firings up to 2026-11-10 re-read this body in full. Many nodes in the bucket carry an "examined and deliberately left without an instrument" note for the same reason: the bucket re-presents them every pass.

**What none of this touches.** This candidate's open question is whether the operator answers asks. The ask queue has gone from 59 to 69 entries, every one with no recorded age and none answered. The counts above say the items are correctly described as asks; they say nothing about whether routing would get any answered.

**Why this node has no instrument.** A command could assert the lane exclusion exists, but that measures the de-duplication repair and not the belief this candidate staked.

_Sources: this vault's own sweep responses, frontmatter greps, node bodies read through `ost_read_tree`, and `ost_read_repo` reads and probes of the product repository, across firings from 2026-08-30 to 2026-11-10. First-party structure; it grounds feasibility, not desirability. Nothing was executed, and no instrument, lane, rung or status was ever changed by these notes. `ost_check` is withheld on the unattended surface, so none of these writes was verified by the invariant checker._

## Definition of done — and it is not a command

"Count how many routed asks the operator answers in the four weeks after they arrive with an age on them"

No command: this one is humans-required on purpose. The bar is **at least 5 of the routed asks answered within 4 weeks**. An exit code can prove the entries moved queues; it cannot observe whether anybody answered them, and whether they get answered is the entire belief this candidate rests on. The half that decides the verdict is why an unanswered entry went unanswered — mis-filed, too expensive, or no longer interesting — and no artifact on disk carries that reason.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

## History
- 2026-11-10 body edited, dropping `## 2026-08-30 — a first-party count of what the bucket it proposes to re-file is actually made of`, `## 2026-09-01 (later firing) — "instead of" is the wrong word: for most of these the routing has already happened, into both queues at once`, `## 2026-09-01 (later firing) — the residue this node treats as an unknown quantity is now composed, and it supports the candidate on correctness`, `## 2026-09-03 — the census's own stated limit on the shown page is closed: 25 of 25, zero instrumentable`, `## 2026-09-07 — the missing lane check is confirmed in the code, and the repair is one line in a function that already imports the predicate`, `## 2026-10-11 — the one-line lane exclusion named on 2026-09-07 has not landed, 34 days on`, `## 2026-10-19 — since 2026-09-01 the bucket has grown only through tests labelled correctly`, `## 2026-10-31 — the repair still has not landed, and firings keep paying to re-check it`, `## 2026-11-07 — cheap check from the 2026-10-31 note: still not landed` — Nine dated follow-up sections (2026-08-30 to 2026-11-07) had grown this node to 31KB, and at least five consecutive unattended firings re-read all of it to re-derive one unchanged verdict; their own transcripts then came back as new evidence. Folded the nine into one standing finding that opens with the cheap check. The candidate's own prose and its Definition of done are reproduced verbatim; every distinct count and code finding is kept; git holds the prior text.

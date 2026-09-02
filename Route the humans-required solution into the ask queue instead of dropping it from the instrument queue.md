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

## 2026-08-30 — a first-party count of what the bucket it proposes to re-file is actually made of

This candidate's premise is that entries in `solutionsMissingInstruments` are mostly items filed in the wrong queue rather than work somebody failed to do. Until now that premise was argued, not counted. This unattended sweep counted a sample of it, and the denominator is stated first because a count without one is the failure this repository's own `src/ost/sweep.ts` exists to refuse.

**What was read.** The bucket held 69 entries; the sweep response showed 25; this pass read 5 of those 25 in full. The sample was taken from the head of the shown list by which titles looked most likely to be repo-answerable — that is, it was deliberately biased *towards* finding instrumentable entries, which makes the result below a conservative one rather than a flattering one. It is not a random sample of 69 and nothing here should be read as a rate over the whole bucket.

**What was found: 5 of 5.** Every one of the five carries an explicit, already-reasoned declaration on itself that no honest instrument exists for it, and the five split into two distinct causes:

- *The artefact is not in this repository.* "A repeated wait on the same condition resumes and doubles its budget automatically, up to a ceiling set once by hand" says the wait helper is supplied by the harness and on the session's PATH, so no spec under this product's `test/` can reach it. "Maintain a running per-item task list the next pass reads before reconstructing state itself" says the same of the harness's task list, and records that a 2026-08-22 pass holding repo sight confirmed it rather than cleared it. "Auto-read a file before the first write or edit to it in a session, instead of erroring" goes further and corrects the routing outright: the guard that produces the observed error belongs to Claude Code, not here, and a 2026-08-22 pass established that the feasibility half separates cleanly while the remaining question is the harness's.
- *The belief is desirability or viability, so an exit code cannot reach it.* "Group the queue by error signature at read time, and change nothing on disk" and "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target" each carry a Definition of done that states in its own words that a command can prove the mechanism emitted something and cannot observe whether anybody trusted or used it.

**Why this strengthens this candidate specifically.** The sibling that filters would remove all five from view. On this sample that would be discarding five correctly-reasoned human-owed decisions, not five pieces of noise — and four of the five have already had a pass spend repo sight to reach their conclusion, so the reasoning being hidden is reasoning somebody paid for. Re-filing keeps that visible and re-labels the claim from a missing command to an owed answer, which on this sample is what it actually is.

**And the give-up this node already states, now with a number against it.** This node warns that routing pours roughly 68 more entries onto a queue standing at 59 unanswered. That queue is now at 60, and all 60 still carry no recorded age. So the risk is not hypothetical and has not improved in the interval: on today's figures this candidate would move 69 items onto a 60-item queue whose answering rate is, so far as anything on disk shows, zero. The count above says the items are correctly *characterised* as asks; it says nothing at all about whether they would be *answered*, and this node's own humans-required test is still the only thing that can.

**One mechanical fact this pass can add that no earlier note carries.** The unattended surface does not hold `ost_flag_humans_required` — it is withheld by design, alongside `ost_check`, `ost_debt`, `ost_gate`, `ost_status`, `ost_deposit` and `ost_rank_source`. So an unattended firing that correctly identifies an entry as humans-required has no call available that records the finding as a lane, and its only remaining options are to annotate prose or to leave the entry alone. That is a sufficient explanation for why this bucket drains at zero across many firings, and it is independent of whether the entries are correctly characterised: even a pass that gets the judgement exactly right cannot act on it. Whoever weighs this candidate should weigh that against the cheaper alternative it does not currently have a sibling for — granting the label call to the unattended surface, which is a permission decision and the operator's alone, not a build.

**Method and limits.** First-party reads of five node bodies through `ost_read_tree` plus repository listings through `ost_read_repo`; nothing executed, no rung moved, no instrument set, no status changed. Grounds only the composition of the sample described above. It says nothing about the 44 entries this surface could not page to, nothing about the 20 shown entries not read, and nothing about whether this candidate beats either sibling — that comparison rests on the answering rate, which is this node's own open test.

## 2026-09-01 (later firing) — "instead of" is the wrong word: for most of these the routing has already happened, into both queues at once

Kept short. One correction to this node's own arithmetic, checked first-party, and it changes what the candidate is.

**The claim being corrected.** This node's 2026-08-30 section reasons about two disjoint piles: an instrument bucket of 69 entries and an ask queue "standing at 59 unanswered", and concludes "on today's figures this candidate would move 69 items onto a 60-item queue whose answering rate is, so far as anything on disk shows, zero." The word doing the work in the title and throughout the body is *instead* — the item leaves one queue and arrives in the other.

**What this firing's own sweep response says.** `outstandingAsks` reports **62**. A grep of this vault's node frontmatter returns **62** files carrying a `lane:` field, every one of them `humans-required`. The two figures are the same set: the sweep defines that queue as every test labelled into a needs-a-person lane or carrying an ask on the ledger, and there are exactly as many labelled tests as there are asks.

**And those same tests still hold their solutions in the instrument bucket.** Verified end-to-end on this node itself, which is the cleanest possible case: "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue" appears in this firing's `solutionsMissingInstruments`; its one assumption carries one test, "Count how many routed asks the operator answers in the four weeks after they arrive with an age on them"; that test's frontmatter reads `lane: humans-required` with no instrument, and it is on `outstandingAsks`. Second case, same shape: "Group the queue by error signature at read time, and change nothing on disk" is in the bucket, and its only test, "Show one operator the grouped queue and the record listing, and record which one they act from", is lane-labelled and on the ask queue.

**So the candidate is not a move, and its stated cost is overstated.** For every entry whose tests are already labelled, the destination queue already holds it — what the bucket shows is the same owed answer counted a second time under a claim that is false about it. Three consequences, and they pull in different directions:

- The give-up this node states most strongly — that it "pours 68-ish more onto" a 60-item queue — does not apply to the labelled majority. Those are already there. What would genuinely be added is only the unlabelled residue, which the sibling census on "The biggest queue on my report is one the surface reading it to me has no tool to clear" measures at 67 tests as of today.
- The work for the labelled majority is therefore **de-duplication, not routing**: honour the lane field the bucket already ignores. That is materially cheaper than this node's "most expensive of the three to build", and it is what the sibling "The split reports defaulted-parked apart from labelled-parked, rather than folding both into one number" already carries an instrument for.
- The zero-answering-rate worry is unchanged and arguably sharpened. All 62 have been on the ask queue with no recorded age, and none has been answered; adding an age column to entries the operator has already not answered is a different bet from putting an unseen item in front of them for the first time.

**What a rewrite of this node would need to say.** The honest title is nearer "stop counting a labelled test twice" than "route it instead". This pass did not rewrite the body, because narrowing a candidate's claim changes what the tree records as having been proposed, and the choice between the three siblings is the operator's.

**Limits.** The 62-equals-62 identity is inferred from two exact counts plus the sweep's own definition of the queue, not from enumerating both lists and matching them title by title; a ledger-only ask with no lane, paired with a lane-labelled test somehow absent from the queue, would preserve the totals and break the identity. The both-queues-at-once claim is verified per file on two solutions, not on all 70. Nothing was executed, no lane set, no rung moved, no instrument set, and this node's humans-required Definition of done stands unchanged.

_Method: this firing's own `ost_next_work` response, one grep over this vault's node frontmatter, and four node bodies read in full. Observed structure of this vault, read first-party; it grounds feasibility, not desirability._

## 2026-09-01 (later firing) — the residue this node treats as an unknown quantity is now composed, and it supports the candidate on correctness

Four lines, per this node's convention. The finding is on the census node and is pointed at rather than restated here.

This node's arithmetic turns on the unlabelled residue: "What would genuinely be added is only the unlabelled residue, which the sibling census on 'The biggest queue on my report is one the surface reading it to me has no tool to clear' measures at 67 tests as of today." That was a size with no composition. This firing enumerated the 67 by name and classified all of them: **46 are people-shaped on their face** (the title names the human act — ask, interview, pitch, sell, publish, show, judge), and of the 21 that are not, **14 have now been examined across passes and every one resolved as already-answered or humans-required in substance**. Zero instrumentable.

**What that does to this candidate, in both directions.** It supports it on correctness — the residue is not work somebody failed to instrument, it is owed answers, so re-filing them as asks states what they actually are rather than relabelling noise. It confirms this node's stated give-up on cost without softening it: routing a residue that is genuinely ~67 asks onto a queue of 62 roughly doubles it, and every one of the 62 still carries no recorded age and no answer. The answering rate remains this candidate's whole open question and nothing here touches it.

_Pointer only. Nothing was executed, no lane set, no instrument set, no rung moved, and this node's humans-required Definition of done stands unchanged._

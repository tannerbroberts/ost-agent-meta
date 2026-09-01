---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
killIf: >-
  A firing still opens a humans-required solution to re-derive why no instrument
  belongs on it, in a pass run after the filter shipped
killBy: '2026-11-30'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A solution whose every test compute may not run holds nothing a builder could start on today]]

**Variation dimension: who-does-the-work. Position taken: nobody — the step is deleted, not reassigned.**

Add one line to `solutionsMissingInstruments` in `src/eval/buildable.ts`: a Solution whose every resolved test sits in a lane `computeMayRun` refuses is not listed. That is the predicate `testsAwaitingVerification` already applies in the same file, so this borrows a rule rather than inventing one, and the two queues stop disagreeing about whether a lane label means anything.

**Why this position and not another.** The sibling candidates both keep the item in front of somebody — one moves it to the ask queue, one makes the exclusion conditional on who set the lane. This one says the listing was simply wrong: the bucket's stated purpose is solutions that "cannot reach a builder, because everything written about it is prose," and a test in the humans-required lane is not prose that failed to become a command. It is a finished decision about who the measurement belongs to. Nothing needs routing, ageing or re-deciding, so the cheapest correct answer is for the queue to stop saying it.

**Cheapest form.** One `continue` guard beside the two already there, importing `computeMayRun` from `src/knowledge/lanes.ts`, plus a row in the doc comment recording why — in the same voice the `shipped` exclusion is already recorded in, since that paragraph exists precisely because the same defect went unexplained once before.

**What it deliberately does not do.** It builds no ask queue, no ageing, no report of what it removed. A reader of the sweep will not learn that these solutions exist at all from this bucket.

**What it gives up, plainly, and this is the sharp cost.** Silence is indistinguishable from correctness. Once excluded, a solution whose lane was set too cautiously — by an agent passing `humansRequired:` at creation because it could not think of a command, which is a real and cheap failure mode — disappears from the one list that would have surfaced it, permanently and with no trace. The sibling that distrusts the bare field is built entirely around that risk; this candidate accepts it in exchange for costing one line. It also does nothing about the 488 tests already waiting on a person: it makes the queue honest, not shorter in any way that gets work done.

**What would make this the wrong pick.** If a meaningful share of the current 68 carry `humans-required` because a pass defaulted there rather than because a person judged it, this filter cements those defaults out of sight and the tree quietly loses tests it should have argued about.

**Honest note on how this was ideated.** The sweep asks for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.

## Definition of done

"An all-cautious solution leaves the instrument bucket while one with a runnable test beside it stays"

```
npx vitest run test/eval/lane-aware-instrument-bucket.test.ts
```

The bar, pre-committed: 0 solutions carrying a compute-runnable test are dropped, and at least 1 all-cautious solution is. The spec does not exist yet, so this command is red for the weak reason — it names a missing file rather than a failing assertion, and an unattended sweep holds no write grant on the product repository to fix that. The threshold is what a builder acts on until the spec is written.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

## 2026-09-01 — the defaulted-label risk this node names, counted for the first time

Kept short, per this branch's convention. Only what is new.

**The risk being measured.** This node's "what would make this the wrong pick" paragraph is specific: if a meaningful share of the bucket carries `humans-required` because a pass defaulted there rather than because a person judged it, this filter cements those defaults out of sight, permanently and with no trace. Nothing on the tree had ever counted that. This pass counted it.

**Method.** A frontmatter census of `lane:` across every node file in this vault, then a solution to assumption to test trace for each bucket entry that states its own no-instrument reasoning — reading the *test's frontmatter* rather than the parent's prose, because a prose declaration and a set lane are different artifacts and this node's risk is about the second. Nothing executed, no rung moved, no instrument set, no status changed.

**Upper bound on this candidate's reach: 62 of 70.** Exactly 62 of the vault's 497 tests carry `lane: humans-required`, and that is the same 62 the sweep reports as `outstandingAsks` — the label set and the ask queue are one set, not two overlapping ones. A solution leaves the bucket under this filter only when every test beneath it is labelled, so this candidate can remove at most 62 of the 70 entries, and fewer wherever a labelled test shares a solution with an unlabelled one. It is close to a complete fix rather than a partial one, which no prior note establishes.

**Hit rate among entries that state their reasoning: 8 of 9.** Of the 25 entries the sweep showed, 9 carry an explicit "no instrument on purpose" declaration in their own body. Eight of those nine already carry the lane label on their sole test, each traced individually this pass:

- "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue"
- "Group the queue by error signature at read time, and change nothing on disk"
- "A human-edited manifest of loop-prescribed call sequences the harvester suppresses"
- "Hand the oversized body to the harness's own compaction and store nothing new"
- "A repeated wait on the same condition resumes and doubles its budget automatically, up to a ceiling set once by hand"
- "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target"
- "Buy the answer from the operator once and print it on expiry, rather than building any way to infer it"
- "Adopt the platform's own job-control wait instead of maintaining a bespoke shell helper"

**The ninth is a class this filter does not reach, and it is worth naming as a class.** "Append-only tool surface with no delete or shell tool" states that no honest instrument exists for it and has never had a lane set. Seven passes declined to instrument it on the reasoning that a red here would be *actively misleading*: a spec asserting "no delete tool" goes red against today's code, but it would be measuring the deliberate absence of a shipped feature, and a builder could pick it up and implement it. So the bucket holds at least two distinct populations — labelled-but-ignored, which this candidate drains, and reasoned-but-unlabelled, which it leaves exactly where it is. The second moves only on a human's `ost-agent lane --set`, or on the (a)/(b) supersession decision that node has been asking for since 2026-08-04.

**What this does to the risk, and it cuts in this candidate's favour.** All eight labelled tests carry a written justification on their parent solution naming why an exit code cannot reach the belief — whether anyone trusts the groups enough to act from them, whether the founder keeps one more list current, whether the operator answers an ask that arrives with a clock on it, whether a compaction silently dropped a retraction. On this sample the labels are reasoned decisions rather than a pass defaulting because it could not think of a command: 8 of 8. That is the first evidence against the failure mode this node names as disqualifying.

**Limits, stated so this is not over-read.** The 25 are the id-ordered head of 70 and 45 entries were not pageable from this surface. The 9 were selected by carrying a declaration, which is precisely the population most likely to have been reasoned, so 8 of 8 is biased toward the flattering answer and is not a rate over the bucket. The 16 shown entries carrying no declaration were not traced and could well be defaults — they are where a sceptic should look, and this pass did not. The 62 upper bound is a count of labels, not of solutions, so the true reach is that number or lower.

_Method: `Grep` over this vault's own node frontmatter, `ost_read_tree` on nine node bodies, and the four assumption-to-test traces named above. Observed structure of this vault, read first-party; it grounds feasibility, not desirability, and no test was run and no result recorded._

## 2026-09-01 — the population this filter does NOT reach is roughly six times larger than the last count found

Kept short, per this branch's convention. Only what is new.

**The errand this closes.** The 2026-09-01 census section above ends by naming exactly where a sceptic should look and declining to look there: "The 16 shown entries carrying no declaration were not traced and could well be defaults — they are where a sceptic should look, and this pass did not." This pass looked, at five of them.

**Result: 0 of 5 are defaults. All five are reasoned, and none is labelled.** Each was already examined individually by a prior sweep holding repo sight, each carries a written reason why no honest instrument exists, and each ends with the identical sentence — that a human should set the lane with `ost-agent lane --set`, because `ost_flag_humans_required` is withheld on the unattended surface.

- "A highlight criteria note the founder edits and the loop reads before deciding what to surface" — examined 2026-08-29; the belief beneath it is viability about one person's behaviour over months.
- "Axioms elicited at the moment a derivation needs them, one accept-or-reject ask at a time" — examined 2026-08-29; viability about an answering rate, and the node names viability as its own sharpest risk.
- "Borrow the axiom set from a named body of practice and let the human only veto" — examined 2026-08-29; desirability about whether veto-only review confers ownership.
- "Monitor states its accepted command grammar up front rather than discovered by refusal" — examined 2026-08-29; the artefact is a harness tool no spec here can reach, and the belief is a counterfactual besides.
- "Name the specific mechanisms a hand process structurally cannot have" — examined 2026-08-31; and it illustrates the asymmetry best, since its feasibility half is already spec-backed and green, so a spec here would re-prove what passes rather than fail today.

**Why the earlier count missed them, which is a correction to the method rather than to the reasoning.** The census above detected a declaration by looking for a "Definition of done" section. These five record their examination as an `## Issues` annotation instead — which is what `ost_annotate` produces, and it is the tool a pass reaches for when recording that it looked rather than when committing to a bar. So the detector was keyed on the wrong heading and the "9 of 25 carry a declaration" figure is a floor, not a rate. On this sample the true figure is at least 14 of 25.

**What this does to this candidate, and it cuts both ways.** In its favour: the defaulted-label failure mode this node names as disqualifying now has 0 hits across 13 traced entries (8 labelled from the earlier pass, 5 unlabelled from this one). Against it: the reasoned-but-unlabelled population — which this filter leaves exactly where it is, because it keys on the lane label — is not the single instance the earlier analysis found. It is at least **6 of the 25 shown** (these five plus "Append-only tool surface with no delete or shell tool"), about 24%. So a lane filter shipped today would quieten the labelled majority and leave roughly a quarter of the bucket recurring forever, each entry carrying a written request for a one-line command nobody has run. That is not an argument against the filter; it is an argument that the filter alone does not close this opportunity, and whoever builds it should expect the bucket to keep returning a residue.

**The cheap move that is not a build.** Five nodes name the same command against themselves. Running `ost-agent lane --set` on those five would move them into the population the filter reaches, before any code is written, and would also test the filter's premise on real nodes rather than on a fixture. That is a human's call and this pass did not make it — the whole point of the withheld tool is that compute does not label its own way out of a queue.

**Limits.** Five of sixteen, chosen for looking repo-answerable rather than at random, so this is not a rate over the untraced set and the remaining eleven are still untraced — six of them are plainly commercial (pricing, cohort, public trial, free-tree offer, interview habit, the two-week comparison) and would be no surprise as humans-required, which if anything means the sceptical residue sits in the other five. Nothing was executed, no rung moved, no instrument set, no status changed, and no node was created.

_Method: `ost_read_tree` on five node bodies, plus first-party `ost_read_repo` reads of `src/eval/buildable.ts` and `src/eval/coverage.ts` in full this pass. Observed structure of this vault; it grounds feasibility, not desirability._

## 2026-09-01 (later firing) — the head is now fully accounted for, and the unreachable residue is a different population than either earlier count guessed

Kept short, per this branch's convention. Only what is new.

**The errand this closes.** The section above ends by naming eleven untraced entries of the twenty-five and declining to trace them: "six of them are plainly commercial … which if anything means the sceptical residue sits in the other five." This pass traced the rest. **All 25 shown entries now carry a recorded, first-party reason why no honest instrument exists. None is un-done work.** The four forms it takes: 14 carry the `## Issues` line "examined for a missing instrument and deliberately left without one"; 8 carry a "Definition of done — and it is not a command" with a bound humans-required bar; 2 ("Auto-read a file before the first write or edit to it in a session, instead of erroring", "Maintain a running per-item task list the next pass reads before reconstructing state itself") carry dated notes from repo-sighted passes establishing the artefact is the harness rather than this repository; and 1 ("Append-only tool surface with no delete or shell tool") carries a standing finding and an (a)/(b) supersession ask open since 2026-08-04. The defaulted-label failure mode this node names as disqualifying is now 0 hits across 25 of 25, up from 13.

**The residue is not where the section above predicted, and this is the correction that matters.** That section reasoned the sceptical residue sits in the five non-commercial untraced entries and that the six commercial ones "would be no surprise as humans-required." The lane census says the opposite. Every non-commercial entry traced this pass turns out to be **labelled already** — its test is one of the 62 and sits on `outstandingAsks` under its own name: the sandbox ask for the background-output candidate, the two Monitor implementation asks, the editor-tool auto-read ask, the task-list ask, the differentia-grading ask. The **commercial** entries are the unlabelled ones. Two were confirmed individually by tracing solution → assumption → test: "Continuous story-based interview habit" rests on "Two-week recruiting test for interview supply" and "Run both for two weeks on the same evidence and publish what diverged" on "Have a second person run the hand arm, so the comparison is not built by its own author", and neither test appears in the 62.

**Why that inverts the advice.** The unlabelled population is not a sceptical residue at all — it is the pre-lane commercial branch, ideated under `agent:P3_ideate` and ported before lanes existed, whose beliefs are recruiting, pricing and willingness to pay. Those are the least contestable humans-required calls on the tree. So the lane filter's reach is better than the 24%-residue estimate implied: what it misses is a small, old, homogeneous set that a human can label in one sitting without adjudicating anything, rather than a quarter of the bucket needing case-by-case judgement.

**One stale instruction found while doing this, worth fixing before it propagates further.** All 14 examination annotations close with the identical sentence: "What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface." For at least six of the 14 the lane is *already set* — the test is on the ask queue — so the sentence is boilerplate that has outlived its accuracy, and a human acting on it would be re-setting lanes that already exist. A future pass writing this annotation should check the test's frontmatter before including that line.

**Limits.** The 25 are still the id-ordered head of 70 and the other 45 were not pageable from this surface; two of the 16 nodes carrying the examination annotation ("Scheduled ambient passes that page the operator only at hard gates", "Show the whole write, exactly as it will land, and require a confirm before it does") are not in the head, so the accounting does reach into the tail, but not systematically. Solution-to-test mapping was confirmed by individual trace for two commercial entries and inferred from title correspondence against the 62 for the rest — that inference is where this section is weakest, and it runs in the direction of *overstating* how many are labelled. The four remaining commercial entries (concierge cohort, the two pricing candidates, the public trial, the free-tree offer) were not traced to their tests at all; they are grouped with the unlabelled set on the strength of no willingness-to-pay test appearing anywhere in the 62.

_Method: `ost_read_tree` on six node bodies, `Grep` over this vault's node frontmatter for `lane: humans-required` (62 files, whole corpus) and for the examination annotation (16 files), and a first-party `ost_read_repo` read of `src/eval/buildable.ts` in full confirming `solutionsMissingInstruments` still applies no lane check while `testsAwaitingVerification` two functions below still does. Nothing executed, no rung moved, no instrument set, no status changed, no node created. Observed structure of this vault; it grounds feasibility, not desirability._

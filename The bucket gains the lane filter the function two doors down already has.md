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

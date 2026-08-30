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

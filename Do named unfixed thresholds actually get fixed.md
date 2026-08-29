---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability).** That naming an unfixed threshold causes it
to get fixed — rather than adding 21 more lines to a report and a standing number
that never moves.

**Why it is the riskiest one here.** The census is not in doubt: 21 of 27 tests in
`tetrix-ost` open their pre-commitment with an imperative, and only 4 of 27 carry a
number or an explicit bound. Both were measured mechanically. What is in doubt is that anybody does anything about it.
Fixing a threshold is not typing — it is deciding, before looking, what would make
you abandon an idea you like. That is the single most avoided act in product
discovery, and a list is a weak instrument against it. This tree has a directly
relevant precedent: three paste-ready verdict commands have sat in
`.ost-agent/drafts/` unrun for five briefings, and those took thirty seconds each.

**Proposed test.** Run the census now and record the count per vault. Publish the
named list once — no reminders, no nagging, no second surfacing. Re-run the census
after two weeks.

**Pre-committed threshold:** at least 6 of the 21 `tetrix-ost` tests carry a number
or a bound two weeks later, with no intervening prompt. Fewer than 3 refutes this and
means the report is not the intervention — at which point the honest next move is
"Refuse to record a result against a threshold that was never fixed" or nothing,
**not** a second, louder report.

**What it does NOT test.** Whether the thresholds people then write are any good. A
number written to clear a list is still a number, and this measures only that one
appeared. It also says nothing about `ost-agent-meta`, whose tests are already mostly
bounded — the effect being measured is on the vault that has the problem.

**Lane: compute-only for the census, humans-required for the fixing.** Counting is
mechanical and repeatable and an unattended pass may run it. The two-week wait and
the decision it is waiting for are not something compute can supply, and a pass that
"helps" by writing thresholds itself would be manufacturing the evidence — the agent
must not fix these.

⚠️ Proposed only — the agent does not run tests or record results.

## Issues
- 2026-08-29 2026-08-29 unattended sweep, repo-grounded. Two findings, and together they resolve what this node should be labelled.

**1. The lane sentence declares two lanes, which is the one construction the ruleset names by example as forbidden.** This node reads "Lane: compute-only for the census, humans-required for the fixing." The ruleset's rule on lanes uses almost that exact sentence as its illustration of the violation: a test must "name exactly one lane", and one naming two is "two tests wearing one node, and the reader refuses it rather than picking a half." The `lane:` frontmatter field is null, so nothing contradicts anything mechanically and `check` has no conflict to report — the ambiguity lives entirely in prose, which is why it has sat here since 2026-07-25 without surfacing.

**2. The compute-only half is not pending work. It shipped.** Read first-party this pass through `ost_read_repo`: `test/eval/unfixed-thresholds.test.ts` exists and exercises `thresholdKindOf`, `askedOf` and `computeUnfixedThresholds` from `src/eval/coverage.js` across four classifications — bound, instruction, prose, absent — including the digit-less-comparator and wrapped-lead-in cases. Its header states the same census this node cites: "21 of 27 open with Fix… / Decide… / Choose…". So the census this node reserves a compute lane for is built, and an instrument pointed at that spec would be green on arrival, which `verifyInstrument` refuses for measuring nothing.

**What follows, and it is a one-command repair a human can make.** With the census half already shipped, nothing compute-runnable remains here. The whole surviving question is the desirability one this node's own title asks — does naming an unfixed threshold cause anyone to fix it, re-counted after two weeks with no intervening prompt — and that is irreducibly a person plus wall-clock. The correct label is therefore `humans-required`, whole, not split:

    ost-agent lane --set "Do named unfixed thresholds actually get fixed" humans-required -w "census half shipped in test/eval/unfixed-thresholds.test.ts; only the two-week human re-count remains"

Not done here: `ost_flag_humans_required` is withheld from this surface, and the ruleset forbids labelling a node whose own prose declares a different lane — the sentence needs fixing by the same hand that sets the label. No instrument was set for the same reason, and none should be.

**Where this node sits in the wider count.** It is one of exactly four assumption tests in this vault that declare compute-only in their prose and carry no `instrument:` field. The other three were examined by earlier firings today and all three are already-answered. This one was not examined before this pass. Bound on that claim: it covers tests that *say* compute-only; a test answerable by compute without declaring so is outside it.

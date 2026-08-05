---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Every published row carries all four factor values as separate visible fields
  — unblock count, believability rung, gate/lane hold, recorded-decision touch —
  and a row that cannot compute one renders it as unknown rather than omitting
  it or defaulting it. No surface emits a combined, weighted or sortable single
  number derived from the four.
instrument: npx vitest run test/ost/factor-table-no-composite.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, with a potential-harm edge that is the real reason to write it.**

**The assumption under test.** Two things at once, and they pull opposite ways. That the four factors are each recoverable from the vault for every row — the parent asserts this and it is checkable — and that the rendering does not, anywhere, collapse them. The second half is the one worth a spec, because a composite score is the easiest thing in the world to add later for convenience, and this tree's own prioritization rules forbid quantified scoring formulas outright. A guard is how a stated rule survives the next person who wants the table sortable.

**Why the unknown-rather-than-default clause matters more than it looks.** The parent's chief risk is that "only what is cheap to compute gets modelled" and that a legible-but-wrong table invites trust an absent one does not. The specific way that goes wrong is a missing factor rendering as a zero or a blank, which reads as a real value. Forcing an explicit unknown is the cheapest thing that keeps the table's gaps visible, and it is a mechanical property with an exit code.

**What is red today.** Nothing renders a factor table, so the first two clauses fail on a missing mechanism. The no-composite clause is the interesting one: it would go red against a straightforward first implementation, because collapsing four columns into one sort key is the obvious way to make a ranked view ranked. Writing it now means the prohibition is committed before the convenience exists to argue with.

**What a green result does NOT settle, and this is the parent's own strongest objection.** The factors that have actually driven this tree's real decisions — the founder's free-distribution call, the evidence-debt gates, the WIP limit, the sequencing of the cold-offer test — are not recoverable from the vault. A green table renders four columns of correct values for a row and still misses the thing that put that row where it is. The gate/decision column is a boolean standing in for a paragraph, and the parent says so. No exit code detects a table that is right about everything cheap and silent about everything that mattered.

Nor does it settle whether an operator forms a better view from factor values than from an order — [[Hand-label the gated rows and check whether a detector agrees]] is the sibling that needs a person's labels.

**Lane: compute-only.** Fixture vault, the four extractors, and a scan of the rendered output; no person is the measurement.

⚠️ Unvalidated. Agent-ideated by an unattended pass. Nothing here was run.

---
type: Solution
source: 'agent-ideated:2026-08-02-unattended-sweep-priority-order'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The factors behind a rank can be detected mechanically, agreeing with a hand labelling]]
[[A row can carry every factor separately without a composite number reappearing anywhere]]

**The mechanism:** the "why" is not prose, it is the inputs. Each row renders the named factors that bear on its position — how many blocked tests one build would unblock, the rung the node rests on, whether a gate or lane holds it, whether a recorded decision touches it — as separate visible values. The operator reads the factor values and forms their own view of the order.

**No composite score, deliberately.** This tree's own prioritization rules forbid quantified scoring formulas and treat prioritization as messy, subjective and reversible; collapsing four factors into one number would smuggle a weighting nobody agreed to and dress a judgement as arithmetic. So the factors are published side by side and the ordering remains a judgement made in view of them — which is also the difference from "Rank every node by how many blocked tests one build would unblock", where one factor silently *is* the order.

**Chief risk, stated plainly:** only what is cheap to compute gets modelled. Every factor above is recoverable from the vault; the reasons that have actually driven this tree's real decisions are not — the founder's free-distribution call, the evidence-debt gates, the WIP limit, the sequencing of the cold-offer test. A factor table would render those rows with a full set of values and still miss the thing that put them where they are, and a legible-but-wrong table is more dangerous than an absent one because it invites trust. The mitigation is that the gate/decision factor is itself one of the columns, but a boolean is a thin rendering of a paragraph.

**Cost shape:** moderate to build (four extractors over the vault), near-zero per pass (recomputed, never re-authored) — the inverse of the ledger candidate's cost curve.

## Definition of done

"The row renders four factor values and emits no composite number anywhere"

```
npx vitest run test/ost/factor-table-no-composite.test.ts
```

Green means each row carries all four factors as separate visible fields, an uncomputable factor renders as unknown rather than as a zero or a blank, and no surface anywhere emits a combined or sortable single number derived from them. The last clause is the one worth committing before the convenience exists to argue with: collapsing four columns into one sort key is the obvious way to make a ranked view ranked, and this tree's prioritization rules forbid quantified scoring formulas outright.

It does not answer this node's own chief risk. The factors that drove this tree's real decisions — the free-distribution call, the evidence-debt gates, the WIP limit, the cold-offer sequencing — are not recoverable from the vault, so a green table can be right about everything cheap and silent about everything that mattered. No exit code detects that, and the gate/decision column stays a boolean standing in for a paragraph.

## History
- 2026-08-05 unlinked "Hand-label the gated rows and check whether a detector agrees" — moved under "The factors behind a rank can be detected mechanically, agreeing with a hand labelling" — the belief this test measures now has a node of its own
- 2026-08-05 unlinked "The row renders four factor values and emits no composite number anywhere" — moved under "A row can carry every factor separately without a composite number reappearing anywhere" — the belief this test measures now has a node of its own

---
type: Solution
source: 'agent-ideated:2026-08-02-unattended-sweep-priority-order'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The mechanism:** the "why" is not prose, it is the inputs. Each row renders the named factors that bear on its position — how many blocked tests one build would unblock, the rung the node rests on, whether a gate or lane holds it, whether a recorded decision touches it — as separate visible values. The operator reads the factor values and forms their own view of the order.

**No composite score, deliberately.** This tree's own prioritization rules forbid quantified scoring formulas and treat prioritization as messy, subjective and reversible; collapsing four factors into one number would smuggle a weighting nobody agreed to and dress a judgement as arithmetic. So the factors are published side by side and the ordering remains a judgement made in view of them — which is also the difference from [[Rank every node by how many blocked tests one build would unblock]], where one factor silently *is* the order.

**Chief risk, stated plainly:** only what is cheap to compute gets modelled. Every factor above is recoverable from the vault; the reasons that have actually driven this tree's real decisions are not — the founder's free-distribution call, the evidence-debt gates, the WIP limit, the sequencing of the cold-offer test. A factor table would render those rows with a full set of values and still miss the thing that put them where they are, and a legible-but-wrong table is more dangerous than an absent one because it invites trust. The mitigation is that the gate/decision factor is itself one of the columns, but a boolean is a thin rendering of a paragraph.

**Cost shape:** moderate to build (four extractors over the vault), near-zero per pass (recomputed, never re-authored) — the inverse of the ledger candidate's cost curve.

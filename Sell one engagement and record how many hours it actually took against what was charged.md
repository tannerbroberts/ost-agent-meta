---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Fee covers hours at the operator's target rate, and at least 30% of the work
  was tool-enabled.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the engagement is worth selling — that the price a team will pay exceeds the hours it consumes by enough to be a business rather than a comfortable trap.

**Risk category: viability.**

**Design.** Sell one engagement at a real price to a real team. Record every hour spent, including setup, interviews, review attendance, and the handover. Compare against the fee. Also record how much of the work was tool-agnostic consulting versus anything the tool specifically enabled.

**Why it is small.** One engagement, and it produces money — the top rung of the ladder — rather than an opinion.

**What it will not cover.** A first engagement is the slowest, and its hours overstate the steady state. The second measure matters more than the first: if nearly all the work was consulting, the tool is not the business regardless of the margin.

A human runs this and records the result.

## Issues
- 2026-08-17 Lane unset, and this sweep could not set it. Humans-required: "Sell one engagement at a real price to a real team" and record actual hours worked — a real sale and real consulting hours, irreducibly human. `ost_flag_humans_required` is withheld on this unattended surface. Left for a human: `ost-agent lane "Sell one engagement and record how many hours it actually took against what was charged" --set humans-required`.

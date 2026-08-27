---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[An operator who must move the window by hand will actually move it more than once]]

**Variation dimension: who-does-the-work. Position taken: the person, not the agent.**

The vault already has exactly this mechanism for one queue. `discovery.target` in `ost.config.yaml` is human-set, has no tool that can write it, and when it is present `ost_next_work` scopes the whole sweep to that branch and reports what the scoping excluded. This solution says: do the same thing for the other capped lists. Add an operator-held window declaration — a prefix, an id range, a date range, or an explicit list of titles — and the firing is shown that slice and told the size of what it was not shown.

**What it deliberately does not do.** It builds no selection policy. There is no rotation, no recency stamp, no cursor, no sampling. The machine never decides which 25 of 419 it looks at, because on this account choosing where a paid firing spends its attention is a prioritisation decision, and prioritisation is the operator's throughout this product. The agent's job is to work the slice well and to report the denominator honestly.

**What it gives up, stated plainly.** Coverage becomes a function of the operator remembering. An operator who sets the window once and never amends it has reproduced today's defect exactly, with the difference that the freeze is now visibly theirs rather than the surface's. That is the trade: the sibling candidates buy guaranteed advance at the cost of the machine choosing; this one keeps the choice human and accepts that an unattended tree can stall on an unmoved cursor. It is the weaker answer to coverage and the stronger answer to authority, and which of those matters more is not something this node can settle.

**Cheapest form.** One config key, read where `discovery.target` is already read, applied as a filter before the cap rather than after it — so the window selects from the whole set and the cap then trims the window, instead of the cap trimming an unfiltered head. Reported alongside the existing `shown`/`total`/`hidden` so a reader can tell a windowed 25 from a truncated 25.

Ideated by an unattended pass on 2026-08-27 against the assigned dimension. Not blind: this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author, which is the condition the blind-ideation rule exists to prevent. Read the three as one author's three answers, and discount their apparent distinctness accordingly.

## Definition of done

"Count how many times the operator amends discovery.target over eight weeks of git history"

No command: this one is humans-required on purpose. The bar is at least 3 distinct operator-authored changes to `discovery.target` over 8 weeks, read out of the vault's own git log — the bet is already running in production and the evidence is already on disk, so this is the cheapest of the three tests to settle and should be settled first. A refuted verdict here retires this candidate for the price of reading a log, before either sibling is built.

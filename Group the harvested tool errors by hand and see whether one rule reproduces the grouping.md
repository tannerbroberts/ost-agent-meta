---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The rule matches the hand grouping on at least 80% of events, with under 10%
  false grouping.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that two failures can be mechanically recognised as the same class. Group too tightly and the counter never fires; too loosely and it starts escalating on routes that merely rhyme, which is worse than the problem.

**Risk category: feasibility.**

**Design.** Take every tool error in the harvested transcripts and have a person group them into classes by hand — the zsh quoting family, the blocked-wait family, the missing-path family, the stale-edit family. Then write the simplest mechanical rule that could reproduce that grouping and measure how it does against the hand labels.

**Why it is small.** The corpus exists and is a few hundred events. The hand grouping is an afternoon and is reusable for anything else that needs to classify friction.

**What it will not cover.** The rule is tuned on the same corpus it is measured against, so its real accuracy is lower than whatever comes out. Holding back a portion of the events would fix that and is worth doing if the first pass looks promising.

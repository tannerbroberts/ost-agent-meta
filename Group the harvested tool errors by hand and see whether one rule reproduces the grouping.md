---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The rule matches the hand grouping on at least 80% of events, with under 10%
  false grouping.
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that two failures can be mechanically recognised as the same class. Group too tightly and the counter never fires; too loosely and it starts escalating on routes that merely rhyme, which is worse than the problem.

**Risk category: feasibility.**

**Design.** Take every tool error in the harvested transcripts and have a person group them into classes by hand — the zsh quoting family, the blocked-wait family, the missing-path family, the stale-edit family. Then write the simplest mechanical rule that could reproduce that grouping and measure how it does against the hand labels.

**Why it is small.** The corpus exists and is a few hundred events. The hand grouping is an afternoon and is reusable for anything else that needs to classify friction.

**What it will not cover.** The rule is tuned on the same corpus it is measured against, so its real accuracy is lower than whatever comes out. Holding back a portion of the events would fix that and is worth doing if the first pass looks promising.

## Issues
- 2026-09-11 2026-09-11 unattended sweep: humans-required in substance but carries no `lane:` field, so its parent solution comes back in solutionsMissingInstruments every pass. The threshold (rule matches the hand grouping on at least 80% of events) is scored against a person's labels, so the labels are the measurement. Having compute produce them would mean the graded party writing its own answer key. A spec could only compute the rule's side, which is not in doubt. Not labelled because `ost_flag_humans_required` is withheld on this surface; the fix is `ost-agent lane --set`. Once a person has produced hand labels and committed them as a fixture, the agreement score becomes a one-spec instrument. Until then no command can be written honestly.

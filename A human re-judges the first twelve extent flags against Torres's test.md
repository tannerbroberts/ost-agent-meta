---
type: AssumptionTest
source: >-
  observation:2026-08-11 first twelve extent flags, unattended sweep
  adjudication
created: '2026-08-11'
evidence: assertion
lane: humans-required
threshold: >-
  At least 6 of the 12 flagged pairings from 2026-08-11 are confirmed by the
  operator as real duplicates or mis-hung parent/child pairs — fewer than 6
  means the assumption fails and the extent rules are mostly routing false
  alarms.
---
#AssumptionTest #unvalidated #evidence/assertion

**The material already exists:** the twelve flagged pairings from 2026-08-11, each carrying the sweep's verdict and named discriminator in an annotation on the flagged node. The operator re-applies Torres's interventional test — name a solution that addresses one sibling and not the other — to each pairing, blind to the sweep's verdict first if they want the cleaner reading.

**Why the bar is half:** the sweep judged 0 of 12 real. If the human confirms fewer than 6, the assumption fails in the direction the first sample points — the rules mostly convert shared provenance into recurring adjudication cost, and stage 2 needs a provenance-aware exemption (one record legitimately grounding several needs) more than the tree needs more flags. If the human overturns the sweep and finds 6+, the pass's own adjudication cannot be trusted to clear these flags, which is worth knowing even more.

**Small and fast:** twelve pairings, one sitting, no instrumentation — the cost is one review session against annotations already written.

A person outside the building is the measurement here: The twelve verdicts under review were written by the pass itself; only a human's independent judgement of the same pairings can grade them without self-grading.

## Fourth occurrence — same 13 flags, no new pairs (unattended sweep, 2026-08-19)

`ost_next_work` reported 13 hygiene issues this pass. All 13 are re-flags of pairs already adjudicated DISTINCT in the 2026-08-11 and/or 2026-08-17 passes (recorded in each node's own `## Issues` section): the five siblings sharing "I don't know what unit of this anyone would pay for" as evidence, "I don't know what unit..." vs its three subset-extent siblings, the two shared-extent pairs from `TRANSCRIPT:49d6b2d3` and `TRANSCRIPT:0459d729`, and the four subset-extent pairs on "The candidate maps all look alike..." and "The agent's repo sight fails mid-pass...". No pair in this pass's list was novel. Re-appending a third "DISTINCT, do not merge" verdict per node adds no information the tree doesn't already have and was skipped this pass for that reason.

The extent-detector has no memory of prior adjudications, so this set will keep resurfacing on every future sweep until a human runs this test and either confirms the standing verdicts (in which case the detector's shared/subset-extent rule should probably stop flagging citations of a single shared source note as evidence of duplication) or overturns one. Worth prioritizing simply to stop the recurring churn, independent of whether any individual verdict changes.

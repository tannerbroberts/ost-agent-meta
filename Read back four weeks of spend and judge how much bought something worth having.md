---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Spend and useful fraction are uncorrelated, or the useful fraction stays above
  50% as spend rises.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption a ceiling makes is that cost is the thing worth bounding — that runaway spend, rather than steady low-value spend, is the shape of the problem. If the loop is not overspending but is spending steadily on invented work, a ceiling caps the bill and changes nothing about the waste.

**Risk category: viability.**

**Design.** Take four weeks of usage traces and the commits they produced. For each week, judge what fraction of the spend produced something a human later acted on, promoted, or referred to — as against nodes nobody has touched since. Plot spend against that fraction.

**Why it is small.** The traces and the commit history both already exist; the work is reading them.

**What it will not cover.** Whether a node was later acted on is a poor proxy for whether producing it was worthwhile, and it penalises recent work that has not had time to be used. The judgement is also the operator's, about their own tree.

A human runs this and records the result.

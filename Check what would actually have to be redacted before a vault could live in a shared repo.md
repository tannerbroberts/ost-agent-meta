---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Under 10% of nodes need redaction, and a stated rule decides the class without
  per-node judgement.
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a discovery vault can share the code's access control. Discovery evidence often includes things that should not sit in a repository every engineer can read — named customers, pricing conversations, interview transcripts.

**Risk category: feasibility.** With a real ethical dimension: this is other people's words.

**Design.** Take this vault and one other, and have a person mark every node whose contents would be inappropriate in a repository the whole engineering team can read. Count them and note what kind of content they hold. Then ask whether the same exercise would be needed on every future node, or whether a rule could decide it.

**Why it is small.** Reading two existing vaults, no build, and it answers a question that decides the approach before anything moves.

**What it will not cover.** These vaults are about the author's own product and contain no third-party interview material. A vault serving a real customer-facing product would have far more to consider, and this is the mildest possible case.

A human runs this and records the result.

## Issues
- 2026-09-11 2026-09-11 unattended sweep: humans-required in substance and unlabelled. The measurement is a person judging which nodes would be inappropriate for a repository the whole engineering team can read. That is a judgement about other people's words, which the node itself flags as the ethical dimension. A secret or path scanner could only count the mechanical subset, and it would under-report exactly the class the test is about (named customers, pricing conversations). No instrument set. The fix is `ost-agent lane --set`, because `ost_flag_humans_required` is withheld on this surface.

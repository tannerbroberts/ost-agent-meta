---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
lane: humans-required
threshold: >-
  at least 2 of the operator's existing hand-held artifacts were amended on >= 2
  separate days
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: humans-required.**

**Why this test and not the obvious one.** The obvious design is to seed a signature-equivalence list and wait a month to see whether it rots. That costs a month and can only be run once. This one is answerable today from evidence already on disk: the operator has been keeping hand-held artifacts in this vault for months — `discovery.target` and the other operator-set keys in `ost.config.yaml` chief among them — and git already records every time one was amended. The sibling branch "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target" proposes exactly this route for exactly this class of belief; this test borrows it rather than inventing a second method.

**The procedure.** Enumerate the config keys and vault files that are human-set by design and that no tool can write. For each, count the distinct days it was amended by the operator. The bar is at least 2 of them amended on 2 or more separate days — that is, evidence of *upkeep* rather than of one initial setting.

**Why the count alone is not the answer.** Two judgements sit inside it that no script makes. Which files count as a hand-held artifact of this kind is a judgement — the vault auto-commits agent writes constantly, so a naive commit count measures the loop, not the person. And whether a given edit was upkeep or a one-off correction is a judgement about intent. Both belong to the operator, which is why this sits in the humans-required lane despite having a mechanical-looking core.

**Sequencing.** Run this before building anything. It is the cheapest of the three tests under this opportunity and the only one whose corpus already exists. A result below the bar retires this candidate outright — for the price of reading a log — and hands the opportunity to the two siblings that ask nobody for anything ongoing.

**What a run of this would leave uncovered.** It is evidence about one person's past behaviour with artifacts that were not this one, and a signature list may be more or less motivating to maintain than a config key — a person who never amended a window might still maintain a list that visibly shortens their own queue every week. It also cannot distinguish "did not maintain it" from "never needed to", which is a real alternative explanation and should be checked against whether the artifact's subject actually changed in the period.

Unvalidated. Agent-proposed 2026-08-30; not run, and no result is recorded.

A person outside the building is the measurement here: A script can list the commits; it cannot decide which files count as a hand-held artifact of this kind, nor whether an edit was the operator's own upkeep or an agent write passing through. The operator is the measurement for both judgements.

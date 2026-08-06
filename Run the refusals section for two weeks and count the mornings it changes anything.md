---
type: AssumptionTest
status: unvalidated
source: 'TRANSCRIPT:6e66c934-24d8-4200-b6f2-7af23002c478'
created: '2026-08-06'
evidence: observed
lane: humans-required
threshold: >-
  At least 6 of 10 mornings produce a recorded action, and week two is not below
  half of week one.
---
#AssumptionTest #unvalidated #evidence/observed

**Lane: humans-required.** The operator's own reading is the measurement, and there is no exit code that stands in for it.

Put the refusals section at the top of every unattended report for ten consecutive firings and record, per morning, whether the operator did anything the section prompted: edited a grant, changed the prompt's scope, cancelled the schedule, or explicitly decided to leave it. "Explicitly decided to leave it" counts as acting — the failure this is looking for is the section going unread, not the operator disagreeing with it.

Measure the second week separately from the first and compare them. A section that produces four actions in week one and none in week two has not passed; it has demonstrated the decay the parent assumption is worried about, and that result is more useful than a flat average that hides it.

**Pre-committed bar:** at least 6 of 10 mornings produce a recorded action, and week two is not lower than half of week one. Below either line, build the narrower version that reports only refusals that are new or whose blocked work has grown, and re-run this against that.

**Why no instrument.** The repository can prove a refusals section renders. It cannot prove anybody read one. Every mechanically checkable part of this solution — that denials are counted, that the section appears first, that it names the abandoned work item — is worth its own spec file and none of them would settle this question, because a section that renders perfectly and is skipped every morning passes all of them.

**What a pass here does not settle.** It measures one operator, who is also the author of the product, on their own vault. That is the weakest possible population for a desirability claim and the result must not be read as evidence that operators generally want this. It also says nothing about whether the four denials it reports were worth reporting; a section that reliably prompts an action on a refusal that did not matter is a success by this bar and a failure in practice.

A person outside the building is the measurement here: The operator's own reading is the measurement — the test counts whether a person acted on a section over two weeks, and no exit code substitutes for that.

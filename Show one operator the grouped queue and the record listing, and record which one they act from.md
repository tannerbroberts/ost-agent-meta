---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
lane: humans-required
threshold: >-
  at least 3 of 5 sessions pick work from the group view without opening an
  underlying record
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: humans-required.**

**The design, kept small and fast.** Render the same unmapped queue two ways from the same data — the current record listing, and a signature grouping with counts and one representative each. Over five separate working sessions, put both in front of the operator and record one thing: did they choose what to work on from the group view, or did they open individual records first? No interview, no rating scale, no opinion asked; the measurement is which surface the decision came off.

**Why this cannot be a spec.** The exit code can prove the groups are emitted and correct. The belief is that seeing them changes what somebody does, and "the reader trusted it enough to act" is not a property of committed code. Reaching for a spec here would answer a different question and report it as this one.

**Why five sittings rather than one.** The first exposure to a new rendering is not representative in either direction — novelty pulls attention toward it, and unfamiliarity pulls trust away. The bar is set at 3 of 5 so that a single session in either direction does not decide it.

**What a run of this would leave uncovered, named in advance.** It measures one operator, who is also this product's author and therefore knows what the signatures mean without being told — a stranger might not group the same errors the same way, and this design does not test that at all. It also says nothing about whether the grouping is *correct*, only whether it is acted on; a reader could act confidently on a grouping that merges two different problems, which is this candidate's stated blind spot and needs a separate check.

Unvalidated. Agent-proposed 2026-08-30; not run, and no result is recorded.

A person outside the building is the measurement here: A person is irreducibly the measurement here: the question is whether a reader trusts and acts on a machine-computed grouping, and no exit code observes belief or a changed decision. Needs the operator, across five sittings.

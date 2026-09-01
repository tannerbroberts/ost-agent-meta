---
type: Solution
source: 'agent-ideation:2026-08-31-unattended-sweep'
created: '2026-09-01'
evidence: assertion
killIf: >-
  Two consecutive months pass in which the median node body grows, measured in
  characters, despite the rule being in force
killBy: '2026-11-30'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A pass that finds nothing decision-changing will write nothing, rather than find something to say]]

**Variation dimension: who-does-the-work. Position taken: nobody does it, because the step is removed.**

No consolidation mechanism, no split, no compaction. The growth stops at the source: a pass that examined a node and found nothing that changes a decision writes nothing to it. Not a shorter note — nothing. The fact that the pass looked is already recorded outside the node, twice over: git holds a commit per write and the usage trace holds a call per read, both machine-recorded and neither costing a future reader anything. The visit log is being written into the node only because that is the cheapest place to put it, not because that is where it belongs.

**Why this position and not another.** The two siblings both accept the accumulation and manage it afterwards — one restructures where it is stored, one compresses it at read time. Both are strictly more machinery than the thing they manage. This candidate observes that the material is largely re-derivable: "an unattended sweep read this node on 2026-08-27 and declined to ideate" is a fact git already holds, and eleven such lines in a body is eleven copies of something nothing was ever missing.

**The rule, stated tightly enough to be checkable.** An append is warranted when it records something a future reader could not otherwise obtain: a new measurement, a corrected fact, a decision, an examination whose *reasoning* would otherwise be re-derived. It is not warranted when it records that a pass occurred, that a prior finding still holds, or that a hold was respected — three shapes this tree's nodes are visibly full of.

**What it deliberately does not do.** It does nothing about the 1,596 nodes already written, and the worst-affected of them are the ones a reader hits today. This candidate stops the bleeding and leaves the wound; if the existing bodies are the actual cost, a sibling is strictly better and this one is worthless.

**What it costs, plainly.** The rule's boundary is a judgement, and it is exactly the judgement an agent is worst at making about its own output — every pass believes its note is the decision-changing one. Worse, it fails silently and in the dangerous direction: a suppressed observation is not visible anywhere, so the failure mode is a finding nobody recorded rather than a body nobody can read, and the second is at least legible. This tree already carries the evidence that per-node conventions of exactly this kind get improvised and then quietly abandoned.

**What would make this the wrong pick.** If passes are appending because the surface makes appending the only cheap write — which it does, appends outnumbering edits seven to one in the 2026-08-31 trace — then a rule telling them not to is asking for restraint where the incentive runs the other way, and the storage or read-path siblings will beat it.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author. The ruleset asks for one blind ideator per assigned dimension and this surface has no grant to run them, so discount their apparent distinctness accordingly. The named dimensions were taken from the sweep and each candidate takes a position no sibling takes; that is a weaker guarantee than blindness.

Unvalidated. Agent-ideated 2026-08-31; a human to review.

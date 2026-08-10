---
type: AssumptionTest
created: '2026-08-10'
evidence: assertion
lane: humans-required
threshold: >-
  At least 3 of 10 candidate probes pre-authorized in writing for unattended
  execution, and the authorized subset judged by the operator as able to settle
  at least one real feasibility guess from this tree.
---
#AssumptionTest #unvalidated #evidence/assertion

**Small, fast test of one belief.** Draft ten candidate environment probes an unattended feasibility pass might run (each described with exactly what it reads, what it could write, and worst plausible side effect). Hand the list to the operator and ask them to mark each: pre-authorized unattended / attended only / never.

**Pass:** three or more pre-authorized, and the operator agrees the authorized subset could settle at least one feasibility guess currently on this tree. **Fail:** the authorized set is empty or answers nothing worth asking — the informative-and-safe intersection this solution needs does not exist for this operator.

**What this does not settle.** Authorization is stated intent about a described probe, not observed comfort after a real unattended run; and it says nothing about building the probe sandbox itself.

A person outside the building is the measurement here: The operator is irreducibly the measurement: pre-authorization is a human grant, and DEC-3's deliberate unbuilt status means their prior must be measured, not assumed.

---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
threshold: at least 1 human-set lane recognised and 0 agent-set lanes accepted
instrument: npx vitest run test/ost/human-set-lane-audit.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The design.** Against a fixture vault, produce the same lane by both routes and ask whether anything distinguishes them. One test gets `humans-required` through `ost_create_node`'s `humansRequired:` argument, exactly as an agent would write it. Another gets it through the CLI's `lane --set` path. Then run the proposed `trustsHumanSetLane` over both and assert it accepts the second and refuses the first. The spec belongs beside `test/ost/shipped-status-audit.test.ts`, which pins the same distinction for the `shipped` field and is the mechanism this candidate is copying.

**Pre-committed bar, stated before running:** at least 1 human-set lane recognised and 0 agent-set lanes accepted. A single agent-set lane getting through refutes the candidate outright rather than calling for a tighter matcher, because a filter an agent can satisfy by writing the right History line is self-certification with an audit in front of it — worse than the bare field, which at least does not claim to have checked.

**This test is where the candidate most likely dies, and that is the point of running it first.** The parent assumption names the failure it expects: both routes may write a History line of the same shape, with no actor recorded, in which case there is nothing to audit and the analogy to `trustsShippedStatus` breaks at exactly the joint it is being borrowed for. Settling that costs one spec and retires the most expensive of the three candidates before anyone builds it. It should be run before the sibling filter is chosen, since a refuted verdict here is also the strongest argument for that sibling.

**What kind of red this is.** `test/ost/human-set-lane-audit.test.ts` does not exist, so this is a `no-spec` red — vacuous in the sense that any question written on that path would be equally red. An unattended sweep holds no write grant on the product repository and so cannot author the failing assertion that would make it a real one. The bound threshold above is what a builder acts on in the meantime.

**What a green here does not settle.** Only that the two writers are separable today. It does not establish that any lane in this vault was in fact human-set — that census is a separate question and, if the answer is none, this candidate excludes nothing and its own kill criterion fires. Nor does it touch desirability or viability.

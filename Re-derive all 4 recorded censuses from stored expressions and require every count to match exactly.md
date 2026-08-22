---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  All 4 recorded censuses must re-derive from stored expressions with 0 count
  discrepancies against a frozen corpus fixture, and the 1 census declaring its
  rows floors must reproduce that declaration. Any silent narrowing — a count
  that differs without the expression refusing — refutes the assumption.
instrument: npx vitest run test/eval/census-expression-fidelity.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold, fixed before the language is designed:** freeze a corpus fixture at the state each census was taken against, encode all **4** censuses recorded on "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time" as stored expressions, and evaluate them. **Every count must match the recorded figure exactly — 0 discrepancies across all 4** — and the census that declares its two rows floors rather than measurements must reproduce that declaration rather than silently returning a total.

The 4 and their recorded figures, so the bar is checkable and not a promise to check something: 113 across 34 sessions (2026-08-06); 83/28 and 42/36 split by denial shape (2026-08-10); 83/28 and 59/50 (2026-08-16); 91/29 and 82/69 (2026-08-21).

**A discrepancy that the expression refuses is a pass; a discrepancy it returns is a failure.** That asymmetry is the whole point of the bar. A language that cannot express a partition should say so and stop, and a builder can then widen it. A language that returns 71 where the prose said 82 has narrowed the measurement without telling anyone, which is the failure mode this candidate's own body names as worse than the staleness it replaces.

**What the spec asserts.** `test/eval/census-expression-fidelity.test.ts` holds the four encoded censuses and a frozen fixture of transcript records, evaluates each, and asserts exact equality against the recorded figures plus a refusal-not-a-number property for the floors case. It sits beside `test/eval/rollup.test.ts` and `test/eval/coverage.test.ts`, which already test derived-figure code in the same suite.

**Read the red honestly.** **No-spec red**: the file does not exist, this surface cannot author it, and today the command fails for a reason no different from any other question written on that path. The bound threshold above is what makes it a usable build permit anyway (`src/eval/buildable.ts` keeps a permit on a `no-spec` run when the threshold is bound). The absent mechanism, named from the code so the builder is not guessing: there is no expression type anywhere under `src/eval/` — `rollup.ts` derives its figures from hard-coded field reads, not from anything a node could store.

**What a green does not settle.** Only that the language is faithful on four known cases, all from one node, all about denial counts. It says nothing about the censuses this tree has not written yet, nothing about whether recomputing at read time is fast enough to sit in a render path, and nothing about whether an operator wants a live number instead of a dated one — that last is a preference no fixture holds.

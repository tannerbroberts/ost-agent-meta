---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: Fully expressible conditions cover at least 70% of refusals actually fired.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the conditions are expressible outside the tool. Any that are not will still be discovered the hard way, so the improvement is real but partial, and its size is exactly the share that can be published.

**Risk category: feasibility.**

**Design.** Enumerate every refusal each mutating call can issue. For each, attempt to state it as a condition a caller could evaluate from information available before calling. Sort into fully expressible, expressible with a caveat, and not expressible. Weight by how often each has actually fired in the usage traces.

**Why it is small.** A read of the refusal paths in the code against the frequency data already captured.

**What it will not cover.** The drift risk — a published copy going stale against the real rules — is untouched by this and is the objection that most threatens the solution. It needs a separate check that the two stay in step.

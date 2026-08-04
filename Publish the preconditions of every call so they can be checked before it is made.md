---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Try to express every refusal this tool can issue as a precondition, and count the ones that resist]]

Every refusal a tool can issue is expressible as a condition over things knowable in advance — this parent exists, this layer may sit under that one, this source has earned at most this rung, this heading is reserved. Publish those conditions as data the caller can read and evaluate before composing a call, rather than discovering them one refusal at a time.

The usage trace shows exactly this shape: three failed calls in a day, all the same refusal, all about an evidence ceiling that was fully determined by the source before the call was written. Nothing about those failures needed a round trip.

**Compared to the alternatives.** Removes whole classes of failure rather than making them cheaper, and it costs nothing at run time once published. It requires the conditions to be genuinely expressible outside the tool, and any that are not will still be discovered the hard way — so the improvement is real but partial. Richer error messages help after the fact; a dry-run mode still spends the round trip.

**What would make this the wrong pick.** Published preconditions are a second copy of the rules, and a second copy drifts. A caller checking against a stale description will be confidently wrong, which is worse than being told no.

## Definition of done

[[Try to express every refusal this tool can issue as a precondition, and count the ones that resist]]

```
npx vitest run test/mcp/refusal-precondition-coverage.test.ts
```

Green means the refusals that can be fully expressed as a caller-evaluable precondition cover at least 70% of the refusals **actually fired**, weighted by the usage traces rather than counted flat. It is red today because no refusal is published as a precondition and nothing enumerates the refusal paths against the frequency data.

**The weighting is the point, not a refinement.** A flat count over every refusal a mutating call *can* issue would be dominated by rare paths and would say almost nothing about what callers hit. The traces already record what fires: the ladder-ceiling refusal alone accounts for five of one day's failures and one of another's, and `no such node` dominated 2026-07-26. Coverage that misses the top few classes is not partial success, it is the shape that leaves the observed cost untouched.

**Scope limit this command inherits, and it is a real one.** Everything measurable here lives on this tool's own surface. Four refusals recorded on [[Two thirds of my calls failed, and each one only told me after I made it]] this pass came from the surrounding harness — a `Monitor` schema, two `Workflow` dialect rejections, a blocked shell composition — and no precondition this project publishes could have covered any of them. Green at 70% of *this tool's* refusals is compatible with most of the caller's actual pain being untouched.

**What green does NOT settle.** The drift risk — a published copy of the rules going stale against the real ones — is the objection that most threatens this solution and this command does not test it at all. That needs a separate check that the published set and the enforced set stay in step, and without one, a green here can decay into a confidently wrong contract.

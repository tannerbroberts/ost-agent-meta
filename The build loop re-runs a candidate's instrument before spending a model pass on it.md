---
type: Assumption
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility belief, and it relocates this candidate's target from where its own prose puts it.

This node's prose closes: "distinguishing this from the sibling requires reading the build loop's own source, which this pass could not do (repo sight unavailable)." A pass with repo sight read it. The distinction the node was waiting on resolves, and neither of the two options it offered is quite right.

**Status is already re-read, so half this candidate is a no-op.** `examples/automation/build-pass.sh` puts every candidate title back through `node "$CLI" buildable "$sol" --vault .` individually before believing it — its own comment says a title that does not survive its own permit check is a parse error, not a build candidate. Nothing caches a node file.

**What is not re-checked is the thing that decides the spend.** `buildPermit`/`permitFrom` in `src/eval/buildable.ts` is pure: it reads the recorded `## Instrument Log` and never executes the command. Re-reading a node tells you what was observed, not what is true now. The module says this plainly — "A recorded observation is a fact about the past, and a permit is a claim about now" — and provides `confirmPermit` to close it, deliberately opt-in "to the caller about to spend something".

Stated so it could be false: before the build loop spends a model pass on a candidate, something re-runs that candidate's instrument and confirms the red still holds.

Evidence it is false, first-party and dated: `buildable.ts`'s own docstring records that on 2026-08-06 the loop spent a full model pass on a solution whose instrument had been green since a merge seventeen minutes earlier. That is the exact failure this node's parent opportunity is about, arriving through a route neither this candidate nor its sibling names.

**Bound on the observation.** `build-pass.sh` was read from the start through its no-build-candidates report branch; the tail was truncated by the reader's cap, so "no `confirm` invocation appears" is bounded to the portion read and is not a proof of absence. That is precisely what the test beneath this should settle.

---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A side-by-side comparison of two processes' output is judgeable in reasonable time]]

Run the modified process alongside the current one over the same inputs, put the two outputs side by side, and let a human adopt or discard based on the comparison — no interruption, because the old process never stops.

**How it differs from its siblings:** the only sibling that produces *evidence* that a workflow change is an improvement rather than assuming it. Slower to adopt, far harder to regress.

**Trade-off:** doubles the compute for every change, and many workflow changes have no comparable output to diff.

**Riskiest assumptions to test:** that two runs over the same input are comparable enough to judge (feasibility); that a human can tell which output is better in a couple of minutes (usability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Timed side-by-side judgement of canary output]] — moved under [[A side-by-side comparison of two processes' output is judgeable in reasonable time]] — the belief this test measures now has a node of its own

## Definition of done

[[Timed side-by-side judgement of canary output]]

`npx vitest run test/eval/canary-parallel-run.test.ts`

The spec asserts the property this node claims as its whole advantage — no interruption, because the old process never stops. Both processes run over identical input, both outputs are captured for comparison, and a canary that errors or diverges leaves the incumbent's result untouched. Red today because no canary harness exists and a changed process simply replaces the old one.

**What a green here does not settle.** Both riskiest assumptions the node names, and they are the ones that decide it. That two runs over the same input are comparable enough to judge is feasibility — a spec can prove the inputs were identical, which is not the same as the outputs being commensurable, and the node already concedes "many workflow changes have no comparable output to diff". That a human can tell which output is better in a couple of minutes is usability, and it needs a human and a clock. The doubled compute cost is also untouched: the suite passing says the harness works, not that anyone will pay twice for every change.

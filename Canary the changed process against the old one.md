---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
---
#Solution #unvalidated
[[Timed side-by-side judgement of canary output]]

Run the modified process alongside the current one over the same inputs, put the two outputs side by side, and let a human adopt or discard based on the comparison — no interruption, because the old process never stops.

**How it differs from its siblings:** the only sibling that produces *evidence* that a workflow change is an improvement rather than assuming it. Slower to adopt, far harder to regress.

**Trade-off:** doubles the compute for every change, and many workflow changes have no comparable output to diff.

**Riskiest assumptions to test:** that two runs over the same input are comparable enough to judge (feasibility); that a human can tell which output is better in a couple of minutes (usability).

Status: agent-originated candidate. Unvalidated.

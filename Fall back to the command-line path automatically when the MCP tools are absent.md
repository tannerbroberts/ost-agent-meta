---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Treat the missing tool surface as a degradation rather than a stop. The evidence says the command line *was still available* in all three toolless passes — so when the MCP surface does not resolve, the pass routes the work it can still do through the CLI, does that work, and reports plainly which capabilities it ran without.

**The trade it makes:** it is the only sibling that produces value from a toolless run, and the fallback path is already deterministic and needs no model. The price is the one this vault worries about most: a pass that quietly does less and still reports a result is [[A failed pass reports success, so my automation can't tell]] waiting to happen. It is only safe if the degraded run is loudly named as degraded — which is exactly what [[A degraded pass has its own name and is not allowed to report a clean run]] exists to enforce, and this candidate should be treated as *depending* on that rather than as standing alone.

**How it differs from its siblings.** Both other candidates end the run. This one continues it. That makes it the highest-value and highest-risk option of the three, and the choice between them is a real judgement about which failure the operator would rather have: a night of no work, or a night of partial work they might mistake for full work.

**Sharpest version:** fall back only for the read-only half of the pass (ingest, check, status, debt) and refuse the write half, so a degraded run can *report* but never *author*. That keeps the risk asymmetry pointing the safe way.

Distinguishing assumption: that the CLI path can actually reach the same vault the MCP surface would have. If the tools are missing because the whole install is wrong, the fallback is missing too.

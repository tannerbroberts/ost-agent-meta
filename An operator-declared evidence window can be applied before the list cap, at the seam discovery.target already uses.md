---
type: Assumption
source: 'agent-ideation:2026-10-01-unattended-sweep'
created: '2026-10-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.**

The belief: a window key in `ost.config.yaml` (an id prefix, for example `TRANSCRIPT:` or `USAGE:`) can filter `unmappedEvidence` *before* the 25-row cap trims it, at the same seam where `discovery.target` already scopes the sweep. The response can then report the windowed total separately from the full total, and nothing else in the sweep changes.

**How it could be false.** The cap could be applied before any config-driven filter runs, so a window would trim an already-trimmed head. Or `done` could be computed over the capped list rather than the full one, in which case a window would quietly change what `done` means. This node's earlier sections give partial grounds against both. The cap is the `listLimit` parameter on `computeNextWork`, and `src/eval/ageing-replay.ts` already passes it as infinity. `test/mcp/scoped-next-work.test.ts` exists for the `discovery.target` path. Neither one shows where an evidence filter would sit relative to the cap.

**Why this one first.** The sibling assumption, that an operator will actually move the window, is humans-required and is answered from git history. This one the repository answers, and if it is false the candidate costs more to build than its body claims.

Unvalidated. Agent-surfaced 2026-10-01; a human to review.

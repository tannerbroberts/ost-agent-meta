---
type: Assumption
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could be false: every invocation of this CLI that could meet a stale or missing artefact is reached through `npm`, so a `prepare`/`pre*` hook fires before it.

**Why this is the load-bearing one for that candidate and not a detail.** The candidate's entire economy is that it builds nothing. If the hooks are not on the path, it builds nothing *and does nothing*, which is worse than either sibling rather than cheaper than both — and it fails silently, so nobody learns that it did not fire.

**Why it is in doubt right now.** `examples/automation/build-pass.sh` invokes `node "$OST_AGENT_DIR/dist/ost-agent.mjs"` directly, six times, and contains no `npm ci` and no `npm run bundle`. That is the committed automation, read first-party. So on today's code this belief is false, and the question is not whether it holds but whether the automation can be routed so that it does.

**What would make it true.** Every CLI invocation in the committed automation reaching the binary through an npm script, so the hook the candidate depends on is structurally guaranteed rather than conventional.

Unvalidated. Agent-surfaced 2026-09-02; a human to review.

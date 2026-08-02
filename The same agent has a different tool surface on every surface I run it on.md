---
type: Opportunity
source: >-
  INBOX:friction/2026-08-01-friction-fifth-straight-scheduled-pass-with-no-ost-mcp-to.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

**The need (operator's voice):** "I scheduled the same maintenance task I run by hand. Locally it has the full tool surface; on the scheduled surface it silently has none — and I only found out by reading a friction note five passes later. I want a run to tell me what it can actually do before it spends an hour proving it can't."

**What was observed (five consecutive passes, machine-confirmed):** The scheduled routine on this vault ran 2026-08-01 with no `ost_*` MCP tools present. Confirmed via ToolSearch (no `ost_*` tools) and ListPlugins (`ost-agent` not listed), so the MCP server never launched. Root cause converged over four filings: the plugin manifest declares `mcpServers.ost-agent`, but this surface sets `CLAUDE_CODE_REMOTE_SKIP_SETTINGS_SYNC=1`, so the repo-committed `.claude/settings.json` that enables the plugin is never applied. The repo-commit fix was attempted four times running and cannot work here by design — enablement has to happen at the environment level, somewhere the repo cannot reach.

**Why it matters:** The pass did not fail. It ran the deterministic CLI surface, reported a clean `check`, and exited looking successful — while the actual mandate (map, ideate, surface assumptions over 212 unvalidated nodes) was untouched. Cost so far: roughly twenty scheduled passes that produced commentary instead of structure. This is distinct from [[Every run ends blocked on a credential only I hold]] (a missing secret, known at the moment it is needed) because here the capability is absent silently and the run has no way to notice.

**Placement note (agent-proposed, needs human confirmation):** Nested under [[The agent has to guess what resources it's actually working with]] as a subset — the parent covers declared project resources and operating constraints, and the agent's own available tool surface is exactly such a constraint, discovered the expensive way. A human may prefer it top-level under the Outcome; it is filed here rather than duplicated.

**Litmus test:** More than one way to address it — a run declares its required tools at start and halts loudly when they are absent; a preflight capability probe written into the run record so a later reader can see what the pass could do; a documented per-surface enablement path; a degraded-mode contract naming what a toolless pass may still legitimately claim; environment-level provisioning that removes the variance. Distinct mechanisms with real trade-offs. Passes.

**Evidence rung:** `assertion` — the source is the agent's own friction filing about its own tooling. No external party involved; floor rung per the ladder's rule, consistent with this tree's retro-labeling convention.

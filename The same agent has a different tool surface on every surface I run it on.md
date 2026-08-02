---
type: Opportunity
source: >-
  INBOX:friction/2026-08-01-friction-fifth-straight-scheduled-pass-with-no-ost-mcp-to.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A run declares the tools it needs and halts loudly when they are absent]]

**The need (operator's voice):** "I scheduled the same maintenance task I run by hand. Locally it has the full tool surface; on the scheduled surface it silently has none — and I only found out by reading a friction note five passes later. I want a run to tell me what it can actually do before it spends an hour proving it can't."

**What was observed (five consecutive passes, machine-confirmed):** The scheduled routine on this vault ran 2026-08-01 with no `ost_*` MCP tools present. Confirmed via ToolSearch (no `ost_*` tools) and ListPlugins (`ost-agent` not listed), so the MCP server never launched. Root cause converged over four filings: the plugin manifest declares `mcpServers.ost-agent`, but this surface sets `CLAUDE_CODE_REMOTE_SKIP_SETTINGS_SYNC=1`, so the repo-committed `.claude/settings.json` that enables the plugin is never applied. The repo-commit fix was attempted four times running and cannot work here by design — enablement has to happen at the environment level, somewhere the repo cannot reach.

**Why it matters:** The pass did not fail. It ran the deterministic CLI surface, reported a clean `check`, and exited looking successful — while the actual mandate (map, ideate, surface assumptions over 212 unvalidated nodes) was untouched. Cost so far: roughly twenty scheduled passes that produced commentary instead of structure. This is distinct from [[Every run ends blocked on a credential only I hold]] (a missing secret, known at the moment it is needed) because here the capability is absent silently and the run has no way to notice.

**Placement note (agent-proposed, needs human confirmation):** Nested under [[The agent has to guess what resources it's actually working with]] as a subset — the parent covers declared project resources and operating constraints, and the agent's own available tool surface is exactly such a constraint, discovered the expensive way. A human may prefer it top-level under the Outcome; it is filed here rather than duplicated.

**Litmus test:** More than one way to address it — a run declares its required tools at start and halts loudly when they are absent; a preflight capability probe written into the run record so a later reader can see what the pass could do; a documented per-surface enablement path; a degraded-mode contract naming what a toolless pass may still legitimately claim; environment-level provisioning that removes the variance. Distinct mechanisms with real trade-offs. Passes.

**Evidence rung:** `assertion` — the source is the agent's own friction filing about its own tooling. No external party involved; floor rung per the ladder's rule, consistent with this tree's retro-labeling convention.

## Evidence — the same wall, four consecutive filings (mapped 2026-08-02)

The node's `source` can carry only one id, so the rest of the series is recorded here. All four are the same agent hitting the same absence and refining the cause each time:

- `INBOX:friction/2026-08-01-friction-third-straight-scheduled-pass-15th-16th-17th-wit.md` — kind `blocked`, filed 12:31Z. Third straight pass (15th, 16th, 17th) with no `ost_*` tools; mapping, ideation and ranking could not run at all, only the CLI. Cause not yet identified — recorded as "session scoped to OST-Agent + ost-agent-meta repos only, no ost-agent MCP server connected."
- `INBOX:friction/2026-08-01-friction-fourth-straight-scheduled-pass-15th-18th-with-no.md` — kind `missing-affordance`, filed 14:35Z. First real cause: `ost-agent-meta` carried no `.claude/settings.json` enabling the plugin, unlike `OST-Agent/examples/vault/.claude/settings.json` which sets `enabledPlugins: ost-agent@ost-agent`. Fix committed.
- `INBOX:friction/2026-08-01-friction-fifth-straight-scheduled-pass-with-no-ost-mcp-to.md` — the node's `source`, filed 17:28Z. The committed fix did not work: this surface sets `CLAUDE_CODE_REMOTE_SKIP_SETTINGS_SYNC=1`, so a repo-committed settings file is never applied here. Names the correct escalation — environment-level enablement, not another repo commit.

**What the series is worth as evidence.** Four filings, one cause, three wrong diagnoses before the right one. The refinement itself is the finding: the surface gave the agent no way to ask "which of my tools exist here", so it could only infer the answer from the shape of its own failures, one pass at a time. That is the need this node states, observed rather than argued.

**Resolved as of this pass (2026-08-02).** The `ost_*` MCP tools are present and this maintenance pass ran the full surface — the first pass in twenty-two to do so. That closes the incident but not the opportunity: nothing was added that would let a future pass detect the same absence, so the next surface with a different environment reproduces it silently. A human should confirm what actually changed (environment-level enablement vs. an incidental difference in this session) before this branch is considered addressed.

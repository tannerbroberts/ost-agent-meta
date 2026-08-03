---
type: Opportunity
source: >-
  INBOX:friction/2026-08-01-friction-fifth-straight-scheduled-pass-with-no-ost-mcp-to.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A run declares the tools it needs and halts loudly when they are absent]]
[[Every run records the tool surface it actually had]]
[[A degraded pass has its own name and is not allowed to report a clean run]]
[[Having the vault is not the same as having the tools, and nothing points that out]]
[[A scheduled run finds out its tools are missing only after it has started]]
[[A helper I installed fails on my own machine's shell, and only running it says so]]

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

## Observed, 2026-08-02 (third maintenance pass) — the streak broke, and the variance moved inside the session

Two facts from this pass, both first-hand and both refining the claim rather than repeating it.

**The five-pass blackout ended.** Passes 15 through 19 ran with no `ost_*` MCP tools at all (friction filed 2026-08-01, refined root cause: `CLAUDE_CODE_REMOTE_SKIP_SETTINGS_SYNC=1` on the scheduled-routine surface, which skips the repo-committed `.claude/settings.json` by design). This pass had the full MCP surface and did structural work with it. Nobody recorded what changed, so the tree cannot say whether a human enabled the plugin at the environment level or whether the surface simply differs run to run — which is itself the shape of this opportunity.

**The variance is finer-grained than "which environment".** Within this one session, with the server connected and eleven `ost_*` tools used successfully, two calls were refused at the permission layer rather than by the server: `ost_check` and `ost_flag_humans_required`. So the agent's real surface is not a property of the environment it wakes up in — it is per-tool, decided at call time, and discoverable only by calling. `ost_check` has now been unavailable to two consecutive passes, which means two passes have written to this vault without confirming its invariants afterwards.

**Why this belongs here and not on a new row:** it is the same need — the agent cannot tell what it is holding until it reaches for it — measured one level finer. The consequence worth a human's eye is that a pass can be *partly* equipped, and a partly-equipped pass looks exactly like a fully-equipped one right up until the call that fails. Evidence class: observed behaviour of this system, self-reported by the agent that hit it.

## Observed instance — 2026-08-02, fourth unattended pass (second consecutive sighting of the same shape)

`ost_check` and `ost_status` were both refused at the permission layer in this session, while every write tool on the same server — `ost_ingest_inbox`, `ost_create_node`, `ost_append_to_node` — worked without a prompt. The third pass this morning recorded the same thing for `ost_check` and `ost_flag_humans_required`. Two consecutive passes, same server, same session type, and the variance is per-tool rather than per-environment.

The sharp part is the direction of the split, which is the opposite of what a safety-minded reader would predict: **the two tools that cannot write anything are the two that cannot be called, and every tool that mutates the append-only vault is available.** So an unattended pass can write six nodes and cannot ask whether it broke an invariant. That is not a variation in capability so much as an inversion of it, and nothing in the pass's own view distinguishes it from a fully-equipped run until the call comes back refused — which is this node's claim, now with a second mechanism behind it: the surface varies not only between environments and not only per-tool, but in a pattern uncorrelated with what the tool can damage.

Filed as observation, not as a request. Whether to grant the read-only tools is the operator's call; the finding here is that the tree cannot see its own tool surface in advance, and three passes have now had to discover it by failing.

## Corroboration — a skill that was not there (unattended sweep, 2026-08-03)

Session `e42cd03d` (2026-07-29) produced this node's failure mode as a single line: `<tool_use_error>Unknown skill: superpowers:subagent-driven-development</tool_use_error>`.

The agent invoked a named capability by its exact identifier, plugin prefix and all — which is what invoking something you believe is installed looks like — and the surface it happened to be running on did not have it. There was no way to find that out other than by calling it. The refusal arrived after the intent had been formed and the call spent.

This is the cheapest possible instance of the problem (one failed call, no side effects) and therefore a good one to reason from: the same gap, hit by a scheduled unattended run rather than an interactive session, is [[A scheduled run finds out its tools are missing only after it has started]].

_Source: `TRANSCRIPT:e42cd03d-b2a4-44ba-989a-9e01cc368f77` — observed behavior, captured mechanically from the agent's own transcript. Grounds usability, not demand._

## Issues
- 2026-08-03 2026-08-03, unattended sweep (second of the day) — two more per-tool refusals on this surface, appended because they sharpen this node's claim rather than repeat it. `ost_check` was declined at the permission layer (fifth consecutive pass) and `ost_flag_humans_required` was declined (third consecutive pass), in a session where every write tool — `ost_create_node`, `ost_append_to_node`, `ost_annotate`, `ost_ingest_inbox`, `ost_next_work` — worked without a prompt. The pattern is now stable enough to state as a shape rather than an incident: on this surface the tools that cannot change anything are the ones refused, while the tools that can write are granted, and the pass cannot discover which is which until the call fails. The concrete cost this pass: two of the three assumption tests it created are compute-only by construction and both are reported under `needsHumans`, because the one call that would have labelled the third was refused and no lane could be written for any of them.

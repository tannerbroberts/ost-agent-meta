# Friction (missing-affordance): Fifth straight pass (15th–19th) with no ost_* MCP tools — the eighteenth pass's fix shipped (commit 82260d6) and did not restore the tools; the diagnosis was wrong, not incomplete, and the real gap is the session's execution surface, not either repo

- **kind:** missing-affordance
- **filed:** 2026-08-01T15:32:24.000Z
- **filed by:** session

**Context:** `ost-agent-meta` already carries `.claude/settings.json` with
`"enabledPlugins": {"ost-agent@ost-agent": true}` (commit `82260d6`, landed after the
eighteenth pass's diagnosis, exactly as that pass proposed). This session — a
scheduled Claude Code Remote routine — still has no `ost_*` tools. Checked directly:
`ListPlugins` (claude.ai org plugins) and `ListConnectors` (MCP connectors attached
to this session) both return empty results, independent of what either repo's
`.claude/settings.json` declares. That file's `enabledPlugins`/`extraKnownMarketplaces`
keys are read by the local Claude Code CLI's own marketplace resolver, which clones
the marketplace and spawns `node ${CLAUDE_PLUGIN_ROOT}/dist/ost-agent.mjs mcp` as a
subprocess of that CLI process. A Claude Code Remote session has no such resolver —
its MCP tool surface is whatever the platform attached to the session at launch
(here: only `Claude_Code_Remote` and `github`), not anything a repo commits. No
commit to either repo can add `ost_*` tools to a Remote session. Fixing this needs a
human to attach the ost-agent MCP server to this environment/session at the platform
level (an org-level plugin or connector), or to run this maintenance loop through a
local Claude Code CLI session instead of a Remote scheduled routine.

Filed by the agent at the moment of friction. Evidence class: **observed behavior** — self-reported by
the product's own agent, so it grounds usability, not demand, and is subject to whatever this agent
failed to notice or chose not to file.

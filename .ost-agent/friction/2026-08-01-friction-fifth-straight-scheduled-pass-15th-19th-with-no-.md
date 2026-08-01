# Friction (missing-affordance): Fifth straight scheduled pass (15th-19th) with no ost_* MCP tools -- the 18th pass's fix (commit .claude/settings.json enabling ost-agent@ost-agent into ost-agent-meta) shipped and merged, but did not restore the tools: this session's project root is /home/user, the parent of both OST-Agent and ost-agent-meta checkouts, not ost-agent-meta itself, so ost-agent-meta/.claude/settings.json is never the active session settings regardless of its content. CLAUDE_PROJECT_DIR and CLAUDE_PLUGIN_ROOT are b…

- **kind:** missing-affordance
- **filed:** 2026-08-01T16:30:10.224Z
- **filed by:** scheduled-routine-session-19th-pass

**Context:** Scheduled OST-Agent maintenance task, 19th pass; verified gates (tsc clean, 141 files/1586 tests green), re-ran status/check/debt/channels (241 nodes, 0 violations, 12/91 unfixed thresholds, unchanged since 18th pass), then tested and falsified the 18th pass's unverified fix instead of re-diagnosing from scratch

Filed by the agent at the moment of friction. Evidence class: **observed behavior** — self-reported by
the product's own agent, so it grounds usability, not demand, and is subject to whatever this agent
failed to notice or chose not to file.

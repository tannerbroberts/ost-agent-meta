# Friction (missing-affordance): a pass that dies on a driver error still exits 0 and commits, so automation cannot tell failure from quiet success

- **kind:** missing-affordance
- **filed:** 2026-07-25T02:01:31.714Z
- **filed by:** twenty-passes ambient driver

**Context:** P2_map 2026-07-25T02:00:38Z: SDK auth error recorded in the run journal, yet process exit code 0, commit 8038dfe9 (no changes). A cron schedule would silently no-op forever while looking healthy. The journal knows; the exit code lies.

Filed by the agent at the moment of friction. Evidence class: **observed behavior** — self-reported by
the product's own agent, so it grounds usability, not demand, and is subject to whatever this agent
failed to notice or chose not to file.

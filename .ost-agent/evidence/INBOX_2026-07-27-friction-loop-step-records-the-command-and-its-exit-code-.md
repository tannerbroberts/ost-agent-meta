---
id: 'INBOX:2026-07-27-friction-loop-step-records-the-command-and-its-exit-code-.md'
source: 'INBOX:2026-07-27-friction-loop-step-records-the-command-and-its-exit-code-.md'
title: 2026-07-27-friction-loop-step-records-the-command-and-its-exit-code-
timestamp: '2026-08-02T13:18:53.868Z'
actor: inbox
---
# Friction (missing-affordance): loop step records the command and its exit code but never the directory it ran in, so a recorded failure cannot be reproduced from the record

- **kind:** missing-affordance
- **filed:** 2026-07-27T00:55:14.317Z
- **filed by:** loop

**Context:** Ran 'loop step --phase build -- npx vitest run' from the home dir instead of the repo; vitest collected all four repos and exited 1. The health record shows exit 1 against a command that passes in its intended cwd. The record is honest about the exit code and silent about the one variable that explains it.

Filed by the agent at the moment of friction. Evidence class: **observed behavior** — self-reported by
the product's own agent, so it grounds usability, not demand, and is subject to whatever this agent
failed to notice or chose not to file.

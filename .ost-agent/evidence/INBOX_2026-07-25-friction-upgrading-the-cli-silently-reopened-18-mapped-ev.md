---
id: 'INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md'
source: 'INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md'
title: 2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev
timestamp: '2026-07-25T02:04:25.626Z'
---
# Friction (unclear-rule): upgrading the CLI silently reopened 18 mapped evidence items because done-ness switched from source-scan to a ledger no pass ever wrote

- **kind:** unclear-rule
- **filed:** 2026-07-25T02:04:25.624Z
- **filed by:** twenty-passes ambient driver

**Context:** Same vault, same instant: ost-agent@0.1.3 ost_next_work says 9 unmapped; HEAD build says 27. getMapped() now reads .ost-agent/state/mapped.json which does not exist here, so every historical item re-opened. Second mechanism for the never-done opportunity: doneness accounting is not stable across versions.

Filed by the agent at the moment of friction. Evidence class: **observed behavior** — self-reported by
the product's own agent, so it grounds usability, not demand, and is subject to whatever this agent
failed to notice or chose not to file.

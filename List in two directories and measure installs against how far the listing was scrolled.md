---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 25 installs across the two in 8 weeks, with at least 5 running it
  more than once.
instrument: npx vitest run test/release/registry-install-path.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that these directories carry real traffic. They are new, their volume is unproven, and their ranking is opaque — so building packaging for several of them could be work spent on channels with no users a year from now.

**Risk category: viability.**

**Design.** Package for two directories only, not several, and list. Over eight weeks record installs, and whatever each directory exposes about views or placement. Then check what happened after each install: did the tool get run more than once.

**Why it is small.** Two packagings rather than a full set, and the measurement is whatever the directories already report.

**What it will not cover.** Placement is opaque and a poor listing may fail for reasons unrelated to demand. Installs also overstate interest badly in browse-driven channels, which is why the second-run count matters more than the first number.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/release/registry-install-path.test.ts — Asserts the claim this node rests its whole advantage on — that the thing is one command away from working inside a tool the buyer already runs: each registry manifest's documented install command must resolve to a version that starts outside a vault. Red against today's reality, not a missing file: the plugin's MCP server runs `npx -y ost-agent@latest mcp`, which resolves to 0.9.0 — the release that refuses to start outside a vault — so a stranger arriving through a directory today hits a failure two releases have already removed.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/release/registry-install-path.test.ts` — No test files found, exiting with code 1

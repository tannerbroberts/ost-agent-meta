---
type: AssumptionTest
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
threshold: >-
  Every registered subcommand is named in a file under examples/automation/ or
  carries a one-line reason in the unwired allowlist, and the allowlist holds no
  more than a third of the registry. `claim` in neither list fails the run.
instrument: npx vitest run test/cli/unwired-commands.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The registry and the scripts are both text in this repository.

**What the spec asserts.** Read the subcommand registry out of `src/cli/`, read every file under `examples/automation/`, and partition. Then two assertions:
1. Every registered subcommand is in one of the two sets — script-named, or allowlisted with a reason. `claim` is in neither today, so this fails on the current tree and is the assertion that makes the run meaningful.
2. The allowlist is at most a third of the registry. This is the assumption's real bar: an exemption list holding most of the CLI is not a statement, it is a formality, and the rule this test defends would be worthless at that size.

The second assertion is a threshold rather than a guard, and it is pre-committed here so nobody sets it after seeing the number.

**Why it is red today, stated precisely.** `test/cli/unwired-commands.test.ts` does not exist and neither does the allowlist file, so this run is **`no-spec`** and mints no build permit. Named honestly because the distinction matters: a missing file is red for a reason that has nothing to do with this question. Once the spec exists it goes red for a reason that does — `claim` unlisted — and green only when the wiring or the exemption is written.

**What a green here does not settle.** That a named subcommand is actually executed. The rule checks a string appears in a script; a command mentioned in a comment, in an unreachable branch, or behind an env flag nobody sets satisfies it. It would have caught `claim`, which appears nowhere, and it will not catch the variant that appears once and never runs. It also says nothing about the MCP tool surface, which has the same exposure and no equivalent script.

⚠️ Unvalidated. Agent-proposed; not run.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-11 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-12 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-13 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-14 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-15 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-16 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-17 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-18 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-19 **no-spec** (exit none) `npx vitest run test/cli/unwired-commands.test.ts` — test/cli/unwired-commands.test.ts does not exist — no spec was collected, so nothing was measured

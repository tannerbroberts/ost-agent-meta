---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At least 1 prompting command across the 3 automation files lacks its
  documented non-interactive flag; exactly 0 refutes.
instrument: npx vitest run test/preflight/noninteractive-flag-lint.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What this settles.** Whether the defect is in the checked-in scripts, where a lint can reach it, or only in commands composed at run time, where it cannot. Parse each command in `examples/automation/autonomous-pass.sh`, `build-pass.sh` and the `run:` blocks of `github-workflow.yml`; for each whose executable is on a known-prompting table (`cp`, `mv`, `rm`, `ln`, `git`, `npm`, `gh`), check whether it carries that tool's documented non-interactive flag; report the count.

**Pre-committed threshold:** at least 1 prompting command across the 3 files lacks its flag. Exactly 0 refutes the assumption and, with it, the premise of this whole candidate — the scripts are already clean and the observed prompt came from a surface a script lint cannot see, which is a result worth recording precisely because it redirects effort to the two run-time siblings.

**Why the spec fails today.** No flag table and no command parser exist. `test/preflight/` checks the scripts for other properties, and nothing in the repository enumerates commands by executable or knows which flag suppresses which tool's prompt. The named spec has to build both, which is the behaviour this solution proposes.

**Stated so it is not over-read: this is a no-spec red.** The file below has not been written, so today it fails as any unwritten file does. It carries a bound bar, which is what makes it a working build permit rather than a vacuous one. A builder's job is the table, the parser and the count — the refusal half of the solution is a second step this test does not reach.

**What a green here does NOT settle.** Only that the lint has something to find. It does not settle whether refusing the firing is the right response (a warning may be better), whether the flag table stays current as tools change, or whether the share of prompts originating in ad-hoc mid-run commands is large enough to make this candidate marginal even when it works. Feasibility only.

**Category:** feasibility.

## Instrument Log
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-23 **no-spec** (exit none) `npx vitest run test/preflight/noninteractive-flag-lint.test.ts` — test/preflight/noninteractive-flag-lint.test.ts does not exist — no spec was collected, so nothing was measured

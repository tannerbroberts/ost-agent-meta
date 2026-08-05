---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/config/toolless-preflight.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility**, in its most basic form — can the mechanism run at all in the situation it exists for.

**The assumption under test.** That a pass on a degraded surface retains enough capability to detect its own degradation and halt. This is not obvious and it is the whole candidate: the check must run in exactly the environment where the thing being checked is missing. If the halt is implemented inside the plugin that fails to load, it never executes and the pass proceeds silently — the failure it was built to stop, now with a check that appears to be protecting against it.

**The test (reproduce the degraded surface deliberately).** Recreate the observed condition: a scheduled run with `CLAUDE_CODE_REMOTE_SKIP_SETTINGS_SYNC=1` and the plugin not enabled. Run the pass with a prototype required-tools check in each of the three plausible homes: (a) inside the plugin, (b) in the task prompt as an instruction to the session, (c) in an outer wrapper script that runs before the session starts. Record for each whether the check executed and whether the run exited non-zero.

**Pre-committed threshold.** **At least one placement must halt reliably across 3 of 3 trials.** If none does, the candidate is closed and its sibling "Every run records the tool surface it actually had" becomes the answer by default, since recording after the fact does not require the capability to be present at decision time.

**What a result must also state.** Which placement worked, because that is the buildable artefact. Also whether placement (b) — instructing the session to check itself — held, since that is the cheapest and is also the one exposed to "The agent narrows its own capability to get past a gate I set".

**Who runs it.** A human, or an attended session with scheduling rights. This pass proposes the design only.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/config/toolless-preflight.test.ts — Runs the declared-tools preflight in a session with none of the tools present and asserts it still reports which are missing rather than failing to run; fails today because no preflight exists.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/config/toolless-preflight.test.ts` — No test files found, exiting with code 1

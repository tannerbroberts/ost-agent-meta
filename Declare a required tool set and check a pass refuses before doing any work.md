---
type: AssumptionTest
created: '2026-08-06'
evidence: assertion
threshold: >-
  Required-missing produces zero vault writes and names the absent tool;
  would-use-missing completes normally.
instrument: npx vitest run test/mcp/preflight-required-tools.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption under test (feasibility).** That a pass's required tool set is knowable before its first call, and separable from the set it would merely use.

**The test.** Build a pass context whose available tool list is missing one declared-required tool, and assert the pass exits before performing any vault write. Then build one missing only a would-use tool, and assert it proceeds. The second half is what stops the check from being a blanket refusal.

**Pre-commit before running:** the required-missing case must produce zero vault writes and name the absent tool in its exit message; the would-use-missing case must complete normally. Either half failing refutes this — a check that cannot tell the two apart is not worth having.

**What this does NOT settle.** Whether the required/would-use split is drawn correctly for real passes. A spec proves the mechanism honours whatever split it is handed; whether that split matches how maintenance passes actually branch is a judgement about this product's own workflow, and no exit code reports on it. Desirability, viability and usability are untouched.

**Lane: compute-only.**

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/mcp/preflight-required-tools.test.ts` — No test files found, exiting with code 1

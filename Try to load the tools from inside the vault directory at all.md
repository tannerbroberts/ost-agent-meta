---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  A vault opened from an unrelated working directory yields its tools,
  demonstrated once, within one afternoon.
instrument: npx vitest run test/mcp/vault-declared-tool-load.test.ts
authorship: machine
---
#AssumptionTest #feasibility #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that the host's plugin model will load a tool server declared from within the vault itself, rather than from the project directory the session happened to open. The whole candidate rests on this being possible, and it may simply not be.

**How it would run:** build the smallest thing that would prove it — one vault carrying its own declaration, opened from an unrelated working directory, and see whether the tools appear. No packaging work, no migration, no polish.

**Why it is worth running before the others:** this is the only candidate of the three that survives the vault being moved or opened from an unexpected directory, which is the class the observed failure belongs to. It is also the most invasive to build. A negative answer here is cheap and removes the most expensive option from the consideration set, which is the best outcome a test of this kind can have.

An afternoon at most. If it takes longer than that to answer, the answer is effectively no. Proposed by the agent; a human runs it and records the outcome.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/mcp/vault-declared-tool-load.test.ts — The threshold — "a vault opened from an unrelated working directory yields its tools" — is a property of committed code, not of anyone's afternoon: the spec builds a vault fixture carrying its own tool-server declaration, resolves the server with the process working directory set somewhere unrelated, and asserts the ost_* surface comes back. It fails today because nothing in the repository reads a tool declaration out of a vault.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/mcp/vault-declared-tool-load.test.ts` — No test files found, exiting with code 1
- 2026-09-01 **green** (exit 0) `npx vitest run test/mcp/vault-declared-tool-load.test.ts` — ✓ loading those tools from an unrelated working directory > a declaration naming an artefact that is not on disk fails here, not at launch 368ms [spec 0ce04a81f9d2]

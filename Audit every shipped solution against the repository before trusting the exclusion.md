---
type: AssumptionTest
created: '2026-08-06'
evidence: assertion
threshold: >-
  Every shipped solution resolves to real code in the product repo AND carries a
  History line stating the evidence for the promotion; one failure refutes.
instrument: npx vitest run test/ost/shipped-status-audit.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption under test (feasibility, with a safety edge).** That `status: shipped` in this vault currently means built, so excluding those solutions hides nothing that still needs chasing.

**The test.** For every solution marked `shipped`, resolve the modules and specs its own `## History` or body names — `src/ost/node.ts` and rule `wrapped-wikilink`, the Vault write guard, the `uncovered` field — and assert each is present in the product repository. Assert also that every `shipped` status carries a History line stating the evidence for it, since an unexplained promotion is the shape the dodge would take.

**Pre-commit before running:** all currently-shipped solutions must resolve to real code, and all must carry a reasoned History line. A single one that does not refutes the assumption and the exclusion rule must not ship without a gate in front of the status field.

**What this does NOT settle.** Whether the shipped code does what its node claims — resolving a module proves it exists, not that it is correct. And nothing here bears on whether the exclusion makes the queue more useful to a human, which is desirability and needs a person reading a shorter queue.

**Lane: compute-only.**

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/shipped-status-audit.test.ts` — No test files found, exiting with code 1

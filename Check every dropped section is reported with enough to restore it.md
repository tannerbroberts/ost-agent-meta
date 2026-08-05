---
type: AssumptionTest
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Every entry in the response's `dropped` list carries either the section's full
  prior text or a git ref at which it can be read. A `dropped` entry with
  neither fails the test, and so does a mutating response with no `dropped` key
  at all — absent must be distinguishable from none.
instrument: npx vitest run test/mcp/mutation-response-dropped-sections-recoverable.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Replacement node — full prose arrives with the merge that folds in the mis-cited original.

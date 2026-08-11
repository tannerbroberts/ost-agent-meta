---
type: AssumptionTest
created: '2026-08-11'
evidence: assertion
threshold: >-
  The rollup, the next-work excerpt server, and the standing briefing all
  produce their bounded output through the one distill primitive, and the
  surface census finds zero bounded surfaces bypassing it.
instrument: npx vitest run test/compression/one-primitive.test.ts
---
#AssumptionTest #compression #unvalidated #evidence/assertion

Implement distill(source, budget, goal) and convert the three named surfaces to produce their bounded output through it. The spec asserts both directions: the three surfaces produce byte-identical (or contract-equivalent) output through the primitive, and a census of bounded surfaces finds none that constructs a capped output outside it. If a surface cannot convert without a surface-specific escape hatch in the primitive, the assumption is falsified for that surface and the escape hatch is the evidence.

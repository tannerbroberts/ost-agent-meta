---
type: AssumptionTest
created: '2026-08-11'
evidence: assertion
threshold: >-
  Every registered compression surface declares the decision-fields contract its
  verdict reads, and the harness proves each bounded output preserves that
  contract, with zero surfaces exempt and at least the rollup, next-work
  excerpts, and capped-list surfaces registered.
instrument: npx vitest run test/compression/fidelity-contract.test.ts
---
#AssumptionTest #compression #unvalidated #evidence/assertion

Build a registry of the product's compression surfaces (mirroring the sense census, but for bounded outputs), have each entry declare the downstream decision it serves and the fields that decision reads, and run a harness that verifies — over real and adversarial inputs — that the bounded form still carries those fields. The test passes only when every registered surface has a contract and every contract is proven preserved; a surface that cannot state its contract is itself a finding (it is the assumption being wrong, localized).

## Instrument Log
- 2026-08-11 **red** (exit 1) `npx vitest run test/compression/fidelity-contract.test.ts` — ❯ test/compression/fidelity-contract.test.ts (10 tests | 2 failed) 3532ms
- 2026-08-11 **green** (exit 0) `npx vitest run test/compression/fidelity-contract.test.ts` — Duration  4.08s (transform 161ms, setup 0ms, collect 247ms, tests 3.64s, environment 0ms, prepare 31ms)

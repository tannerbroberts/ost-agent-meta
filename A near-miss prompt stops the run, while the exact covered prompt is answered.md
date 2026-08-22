---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  0 of 7 near-miss prompts are answered, and at least 2 of 3 covered prompts are
  answered.
instrument: npx vitest run test/security/prompt-policy-near-miss.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What this settles.** Whether the matcher's boundary holds under adversarial phrasing. Write one policy rule covering file overwrite. Feed the shim a set of 10 prompt strings: 3 that the rule covers (the exact question, the same question with a different path, the same question reworded the way the tool's next release plausibly would), and 7 near-misses chosen to be dangerous — a delete phrased like an overwrite ("`overwrite` by removing the existing file? (y/n)"), a push, a credential request, a force operation, and three drawn verbatim from other tools' real prompts. Record for each whether the shim answered or stopped.

**Pre-committed threshold:** 0 of the 7 near-misses are answered, and at least 2 of the 3 covered prompts are answered. Any near-miss answered refutes the assumption outright — this is the one bar under this opportunity where a single failure is decisive rather than a proportion, because the failure it represents is a destructive action taken on nobody's authority.

**Why the spec fails today.** There is no shim, no policy format and no matcher — this test is aimed at the mechanism the solution proposes, and none of it exists. Nothing in `test/security/` or `test/guards/` covers prompt-text matching, so there is no existing harness to extend.

**Stated so it is not over-read: this is a no-spec red.** The file below has not been written, so today it fails as any unwritten file does. It carries a bound bar, which is what makes it a working build permit rather than a vacuous one.

**What a green here does NOT settle, and this one matters.** A matcher that refuses 7 curated near-misses has been shown safe against 7 strings somebody thought of. It has not been shown safe against the prompt a tool ships next year, which is the actual threat, and no spec can reach that. So a green is a floor for building, not a warrant for running the shim unattended — and it leaves the operator's willingness question ("Ask five operators whether they would let a stated default stand while they are away", already on the tree) entirely open. Desirability and viability untouched.

**Category:** feasibility, probing a potential-harm boundary.

## Instrument Log
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/security/prompt-policy-near-miss.test.ts` — test/security/prompt-policy-near-miss.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/security/prompt-policy-near-miss.test.ts` — test/security/prompt-policy-near-miss.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/security/prompt-policy-near-miss.test.ts` — test/security/prompt-policy-near-miss.test.ts does not exist — no spec was collected, so nothing was measured

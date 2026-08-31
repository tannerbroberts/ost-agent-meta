---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
threshold: zero windowed responses omit the unit field
instrument: npx vitest run test/product/repo.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What the spec must assert.** Against `readProductRepo` in `src/product/repo.ts`:

1. A read passing `offset` and `limit` returns exactly `limit` units of content starting at `offset`, and the response carries a **`unit` field naming what was counted** — `"characters"`, not left implicit. Today the function accepts neither parameter and returns no unit, so this fails on the shape rather than on a missing file.
2. **Zero windowed responses omit `unit`.** Assert it on the truncated case, the untruncated case and the windowed case alike, so the field cannot be present only where it is convenient.
3. A `limit` larger than `MAX_FILE_CHARS` is clamped to the cap and the response says so, rather than appearing to honour a request it did not.

**Why it is red today and red about this specifically.** `test/product/repo.test.ts` exists and exercises this function, so the run resolves a real suite and fails because `offset`, `limit` and `unit` are absent from the input and result types. Reword the question and the assertion moves with it. Until the spec is written the command passes and records nothing — the failing assertion is the deliverable, the path is only its address.

**What a green here does not settle, and it is most of the candidate.** It proves this product can speak the contract honestly in its own units. It does not prove the contract is worth adopting, and it cannot detect the failure the candidate's kill criterion is written against — the harness changing the contract underneath it. That needs a person watching an upstream, which is the sibling assumption named on the parent and not written here.

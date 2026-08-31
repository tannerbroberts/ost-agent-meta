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

**What the spec must assert.** Against `readProductRepo` in `src/product/repo.ts`:

1. A read passing `offset` and `limit` returns exactly `limit` units of content starting at `offset`, and the response carries a **`unit` field naming what was counted** — `"characters"`, not left implicit. Today the function accepts neither parameter and returns no unit, so this fails on the shape rather than on a missing file.
2. **Zero windowed responses omit `unit`.** Assert it on the truncated case, the untruncated case and the windowed case alike, so the field cannot be present only where it is convenient.
3. A `limit` larger than `MAX_FILE_CHARS` is clamped to the cap and the response says so, rather than appearing to honour a request it did not.

**Why it is red today and red about this specifically.** `test/product/repo.test.ts` exists and exercises this function, so the run resolves a real suite and fails because `offset`, `limit` and `unit` are absent from the input and result types. Reword the question and the assertion moves with it. Until the spec is written the command passes and records nothing — the failing assertion is the deliverable, the path is only its address.

**What a green here does not settle, and it is most of the candidate.** It proves this product can speak the contract honestly in its own units. It does not prove the contract is worth adopting, and it cannot detect the failure the candidate's kill criterion is written against — the harness changing the contract underneath it. That needs a person watching an upstream, which is the sibling assumption named on the parent and not written here.

**Lane: not declared here, deliberately.** The question is mechanical and the instrument above is the whole of it, but the sweep that created this node counts it in the needs-a-person lane, and no call on the unattended surface can move it — the permissive label is a human's `ost-agent lane --set`. Stating "compute-only" in prose would assert a permission nothing granted and put the node's own body in conflict with its field.

## History
- 2026-08-31 body edited — The body opened with "**Lane: compute-only.**", which this surface cannot back. The sweep re-run immediately after creation counts this test under assumptionWork.needsHumans, so the prose declaration and the node's actual lane disagree — the two-answers-to-one-question state the lane-conflict rule refuses. This pass holds no ost_check to detect it and no call that can set the permissive lane, which is a human's `ost-agent lane --set`. Removing the claim rather than leaving prose asserting a permission nothing granted. The three assertions, the red-today reasoning and the what-this-does-not-settle paragraph are reproduced verbatim.

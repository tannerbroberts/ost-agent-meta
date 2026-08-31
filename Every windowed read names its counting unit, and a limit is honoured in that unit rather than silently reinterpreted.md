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

**The instrument is GREEN today, and that is a defect in it — stated plainly rather than claimed otherwise.** `test/product/repo.test.ts` exists and passes, so running the command as it stands proves nothing and grants no permit. The three assertions above have not been written into it. The rule is that an instrument must be red when it is written; this one is not, and it becomes a real test only once assertion 1 is in that file, where it will fail because `offset`, `limit` and `unit` are absent from the input and result types in `src/product/repo.ts`.

**Why this form rather than a path that does not exist.** A command naming an unwritten spec file does go red — identically, for every question anyone could write on it — which is filed as `no-spec`, grants no permit either, and tells a builder only "create this file." Naming the existing suite that already covers `readProductRepo` puts the assertions where they belong and makes the red, once written, specific to this question. Neither form is a valid red from a surface that cannot write to the repository, and the deliverable is the failing assertion, not the path.

**What a green here does not settle, and it is most of the candidate.** Once the assertions exist and pass, it proves this product can speak the contract honestly in its own units. It does not prove the contract is worth adopting, and it cannot detect the failure this candidate's kill criterion is written against — the harness changing the contract underneath it. That needs a person watching an upstream, which is the sibling assumption named on the parent and not written here.

**Lane: not declared here, deliberately.** The question is mechanical and the instrument above is the whole of it, but the sweep that created this node counts it in the needs-a-person lane, and no call on the unattended surface can move it — the permissive label is a human's `ost-agent lane --set`. Stating "compute-only" in prose would assert a permission nothing granted and put the node's own body in conflict with its field.

## History
- 2026-08-31 body edited — The body opened with "**Lane: compute-only.**", which this surface cannot back. The sweep re-run immediately after creation counts this test under assumptionWork.needsHumans, so the prose declaration and the node's actual lane disagree — the two-answers-to-one-question state the lane-conflict rule refuses. This pass holds no ost_check to detect it and no call that can set the permissive lane, which is a human's `ost-agent lane --set`. Removing the claim rather than leaving prose asserting a permission nothing granted. The three assertions, the red-today reasoning and the what-this-does-not-settle paragraph are reproduced verbatim.
- 2026-08-31 body edited — Self-check before reporting caught a contradiction this pass introduced: the paragraph was headed "Why it is red today and red about this specifically" and the next sentence conceded the command currently passes. Both cannot be true. The instrument names a spec file that exists and is green, so the command is GREEN today, not red — a reader taking the heading at face value would believe a permit exists that does not. Replacing the false claim with an accurate statement of the instrument's state and why this form was chosen over a non-existent path. No assertion, threshold or limitation was altered.

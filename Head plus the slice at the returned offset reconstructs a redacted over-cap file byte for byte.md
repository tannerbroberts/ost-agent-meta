---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
threshold: zero characters dropped and zero repeated across the join
instrument: npx vitest run test/product/repo.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec must assert.** Write a file longer than `MAX_FILE_CHARS` (20,000) into a scratch repo and read it through `readProductRepo`:

1. The response carries `truncated: true` and a numeric **`nextOffset`**. Today it carries `truncated` and no offset at all, so this fails on a missing field of a shape that otherwise exists.
2. A second call with that `nextOffset` returns the remainder, and **`head + tail` equals the full redacted content exactly** — zero characters dropped at the join, zero repeated.
3. The fixture must include a string `redactSecrets` rewrites, positioned so the redaction straddles the cap. This is the assertion that carries the actual risk: the offset indexes redacted text whose length differs from the file's, and a spec built only from plain ASCII would pass while the real case silently skips a region.
4. A file under the cap returns no `nextOffset`, so the field's presence means truncation rather than being always set.

**The instrument is GREEN today, and that is a defect in it — stated plainly rather than claimed otherwise.** `test/product/repo.test.ts` exists and passes, so running the command as it stands proves nothing and grants no permit. The four assertions above have not been written into it. The rule is that an instrument must be red when it is written; this one is not, and it becomes a real test only once assertion 1 is in that file, where it will fail on `nextOffset` being absent from `RepoReadResult` in `src/product/repo.ts`.

**Why this form rather than a path that does not exist.** A command naming an unwritten spec file does go red — identically, for every question anyone could write on it — which is filed as `no-spec`, grants no permit either, and tells a builder only "create this file." Naming the existing suite that already covers `readProductRepo` puts the assertions where they belong and makes the red, once written, specific to this question. Neither form is a valid red from a surface that cannot write to the repository, and the deliverable is the failing assertion, not the path.

**What a green here does not settle.** Once the assertions exist and pass, it proves resumption is mechanically sound. It says nothing about the candidate's stated main risk — that a reader treats a truncated body as whole — which is behaviour in real sessions, not an exit code. Nor does it touch the harness `Read` that produced this branch's evidence: that reader is not in this repository and no spec here reaches it.

**Lane: not declared here, deliberately.** The question is mechanical and the instrument above is the whole of it, but the sweep that created this node counts it in the needs-a-person lane, and no call on the unattended surface can move it — the permissive label is a human's `ost-agent lane --set`. Stating "compute-only" in prose would assert a permission nothing granted and put the node's own body in conflict with its field.

## History
- 2026-08-31 body edited — The body opened with "**Lane: compute-only.**", which this surface cannot back. The sweep re-run immediately after creation counts this test under assumptionWork.needsHumans, so the prose declaration and the node's actual lane disagree — the two-answers-to-one-question state the lane-conflict rule refuses. This pass holds no ost_check to detect it and no call that can set the permissive lane, which is a human's `ost-agent lane --set`. Removing the claim rather than leaving prose asserting a permission nothing granted. The four assertions, the red-today reasoning and the what-this-does-not-settle paragraph are reproduced verbatim.
- 2026-08-31 body edited — Self-check before reporting caught a contradiction this pass introduced: the paragraph was headed "Why it is red today and red about this specifically" and the next sentence conceded the command currently passes. Both cannot be true. The instrument names a spec file that exists and is green, so the command is GREEN today, not red — a reader taking the heading at face value would believe a permit exists that does not. Replacing the false claim with an accurate statement of the instrument's state and why this form was chosen over a non-existent path. No assertion, threshold or limitation was altered.

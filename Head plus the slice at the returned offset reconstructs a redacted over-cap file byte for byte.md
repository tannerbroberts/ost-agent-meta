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

**Why it is red today and red about this specifically.** `test/product/repo.test.ts` exists and covers this function, so the command resolves a real suite and fails on `nextOffset` being absent from `RepoReadResult` — a failure that changes if the question changes. Until the spec is written the command passes and records nothing; the deliverable is the failing assertion, not the path.

**What a green here does not settle.** It proves resumption is mechanically sound. It says nothing about the candidate's stated main risk — that a reader treats a truncated body as whole — which is behaviour in real sessions, not an exit code. Nor does it touch the harness `Read` that produced this branch's evidence: that reader is not in this repository and no spec here reaches it.

**Lane: not declared here, deliberately.** The question is mechanical and the instrument above is the whole of it, but the sweep that created this node counts it in the needs-a-person lane, and no call on the unattended surface can move it — the permissive label is a human's `ost-agent lane --set`. Stating "compute-only" in prose would assert a permission nothing granted and put the node's own body in conflict with its field.

## History
- 2026-08-31 body edited — The body opened with "**Lane: compute-only.**", which this surface cannot back. The sweep re-run immediately after creation counts this test under assumptionWork.needsHumans, so the prose declaration and the node's actual lane disagree — the two-answers-to-one-question state the lane-conflict rule refuses. This pass holds no ost_check to detect it and no call that can set the permissive lane, which is a human's `ost-agent lane --set`. Removing the claim rather than leaving prose asserting a permission nothing granted. The four assertions, the red-today reasoning and the what-this-does-not-settle paragraph are reproduced verbatim.

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

**Lane: compute-only.**

**What the spec must assert.** Write a file longer than `MAX_FILE_CHARS` (20,000) into a scratch repo and read it through `readProductRepo`:

1. The response carries `truncated: true` and a numeric **`nextOffset`**. Today it carries `truncated` and no offset at all, so this fails on a missing field of a shape that otherwise exists.
2. A second call with that `nextOffset` returns the remainder, and **`head + tail` equals the full redacted content exactly** — zero characters dropped at the join, zero repeated.
3. The fixture must include a string `redactSecrets` rewrites, positioned so the redaction straddles the cap. This is the assertion that carries the actual risk: the offset indexes redacted text whose length differs from the file's, and a spec built only from plain ASCII would pass while the real case silently skips a region.
4. A file under the cap returns no `nextOffset`, so the field's presence means truncation rather than being always set.

**Why it is red today and red about this specifically.** `test/product/repo.test.ts` exists and covers this function, so the command resolves a real suite and fails on `nextOffset` being absent from `RepoReadResult` — a failure that changes if the question changes. Until the spec is written the command passes and records nothing; the deliverable is the failing assertion, not the path.

**What a green here does not settle.** It proves resumption is mechanically sound. It says nothing about the candidate's stated main risk — that a reader treats a truncated body as whole — which is behaviour in real sessions, not an exit code. Nor does it touch the harness `Read` that produced this branch's evidence: that reader is not in this repository and no spec here reaches it.

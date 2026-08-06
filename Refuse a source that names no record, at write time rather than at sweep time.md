---
type: AssumptionTest
status: unvalidated
created: '2026-08-06'
evidence: assertion
threshold: >-
  Every enabled channel's items carry a resolving source or a documented
  asserted exception, and a node citing an unresolvable id is refused with a
  non-zero exit and nothing written.
instrument: npx vitest run test/adapters/source-attribution.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Whether a write is refused is decided by the code that accepts the write.

Two halves, both fixtures.

First, coverage: ingest one item from every enabled channel and require each captured record to carry a source that resolves to a stored record. The usage channel is the case that decides whether "every" survives — its records are aggregates over several sessions, and if it cannot name one source, this spec should assert what it does name instead, so the honest limit is committed to code rather than left in prose.

Second, and the part that matters: attempt to create a node whose `source` cites an id that no stored record carries, and require the write to be refused. Use `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf` — a real string, in four real nodes in this vault right now, resolving to nothing. Today that string was accepted four times and surfaced later as four `unresolved-citation` hygiene issues. A sweep that finds a bad citation afterwards is a different and much weaker product than a write that will not take one, and the gap between those two is exactly what this test measures.

**Pre-committed bar:** every channel's captured items carry a resolving source or an asserted documented exception, and the unresolvable citation is refused with a non-zero exit and no file written.

**What a green run here does not settle.** It proves a source string points at something. It does not prove the something is what the item actually came from — a record could resolve perfectly and still be the wrong record, and no exit code catches a correct-looking lie. It also says nothing about whether finer attribution makes the tree better, which is the parent opportunity's real claim and needs an operator who has used both.

## Issues
- 2026-08-06 This test's threshold is wrong as written, discovered within the same pass that wrote it. It requires that a node citing `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf` be refused at write time. Later in that same pass the record for `89ac8277` was ingested and all four citations resolved — so the write this test demands be refused was correct, and refusing it would have blocked four good nodes.

The mechanism, now observed rather than inferred: the transcript adapter cannot store a session until that session ends, so a node citing its own live session is born with an unresolvable citation and self-heals at the next harvest. `ost_check` reports that state identically to a citation that names a record which never existed, and those two want opposite responses.

The repair keeps the test's identity and sharpens its bar. A write-time refusal should distinguish three cases, not two: an id that resolves to a stored record (accept), an id that resolves to nothing but names a session file present on disk (accept, and mark it as pending harvest so the hygiene sweep can wait it out rather than report it), and an id that resolves to neither (refuse). The middle case is what this pass walked into and it is checkable — the session file exists before the adapter reads it.

Left for a human because rewriting the prose would re-aim a test toward a bar this pass invented, and because the parent solution's `## Definition of done` names this test by title and quotes the old threshold. Both want changing together.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/adapters/source-attribution.test.ts` — No test files found, exiting with code 1

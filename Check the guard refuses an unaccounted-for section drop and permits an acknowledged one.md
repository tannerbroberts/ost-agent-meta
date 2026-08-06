---
type: AssumptionTest
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Both directions must hold. Refuses when a stored section appears in neither
  `prose` nor `dropping:`, and the refusal message names the section by heading.
  Permits when the section appears in either. A guard that satisfies only one
  direction fails.
instrument: npx vitest run test/mcp/edit-node-unacknowledged-section-guard.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Two calls against the same fixture node, which stores a `## History` section. The first supplies `prose` omitting it and no `dropping:` argument — expect a refusal naming `## History`. The second supplies the same `prose` with `dropping: ["## History"]` — expect it to succeed and the section to be gone.

**Lane: compute-only.** A spec file's exit code settles both directions.

**Why this is red today.** Neither half exists. There is no `dropping:` argument on the rewriting tool, and the omit-and-drop case is precisely what succeeds silently today — observed on 2026-08-05, when a well-formed call destroyed four `## History` entries and returned the same success string it returns for a lossless edit. The permit direction is red for the ordinary reason that the argument is not implemented; the refuse direction is red because today's behaviour is the exact opposite of what is asserted.

**What a green run does not settle, and it is the larger half.** This measures that the guard *can* discriminate on a case someone constructed. It says nothing about the false-positive rate on real work, which is what the assumption above actually turns on — a guard that also fires on every consolidation, retitle, or fold-into-prose becomes noise, and a refusal that mostly fires on honest work is one callers learn to route around. Establishing that rate means replaying this vault's own recorded rewrites and having someone judge which were legitimate, which is a separate test and a slower one.

That distinction is worth holding onto here, because this vault has evidence the noise cost is not theoretical: its own census records thirteen sessions independently rediscovering one refusal, and one session hitting an identical refusal five times in a row. Refusals here are not reliably read even when correct. A green exit code on this spec proves the guard works; it is not evidence that adding another refusal to this surface helps anyone.

## Provenance

First-party observation made during the unattended maintenance pass of 2026-08-05, which reproduced the silent `## History` loss on itself. No stored evidence record exists for it, so the source is free text rather than a citation the vault cannot resolve.

## History
- 2026-08-05 merged "Check the guard refuses a rewrite that omits a stored section and permits one that accounts for it" into this node and deleted its file — Same test, same threshold, same instrument — the original was created minutes earlier in this pass with a fabricated provenance id (`TRANSCRIPT:2026-08-05-unattended-pass`) matching no stored evidence record, which `ost_check` reported as an unresolved-citation violation. `source` is frontmatter with no setter on this surface, so re-creating with truthful free-text provenance and folding the original in is the only available repair. No content changed.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/mcp/edit-node-unacknowledged-section-guard.test.ts` — No test files found, exiting with code 1

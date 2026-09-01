---
type: AssumptionTest
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Every entry in the response's `dropped` list carries either the section's full
  prior text or a git ref at which it can be read. A `dropped` entry with
  neither fails the test, and so does a mutating response with no `dropped` key
  at all — absent must be distinguishable from none.
instrument: npx vitest run test/mcp/mutation-response-dropped-sections-recoverable.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

This test goes at the assumption's crux rather than at the solution's surface. The assumption above is stated against its own solution: that being *told* about a loss is worth little to a caller with no undo. The thing that decides it is not whether a report exists but whether the report is actionable — so this asserts the property that would make the objection collapse.

Perform a rewrite that drops a stored section. Read the response. For each heading in its `dropped` list, assert the response carries either the prior text of that section or a git ref from which it can be read. Separately, perform a lossless rewrite and assert the response still carries a `dropped` key, empty.

**Lane: compute-only.** The exit code settles it; no person is the measurement.

**Why this is red today.** There is no report at all. `ost_edit_node` returns `edited the body of "…"` whether it preserved everything or destroyed a `## History` — the observation from 2026-08-05 that put this branch in the tree. Every assertion here fails against today's code.

**Why the empty-list assertion is not padding.** It is the difference between a caller reading "no sections were dropped" and reading nothing, and the whole failure this branch exists to fix was a loss that looked exactly like a success. A report that appears only when there is bad news teaches a caller that silence means safety, which is the belief that made the original loss expensive.

**What a green run does not settle.** It proves a caller *could* restore. It does not prove one *would*, and it says nothing at all about the risk this assumption's body names as the serious one — that reporting converts a silent loss into a documented one without changing the loss rate, and that a team seeing a tool name its own damage may conclude the damage is handled. That is a judgement about where attention goes, it cannot be read off an exit code, and a human should weigh it before this is built alongside either preventive sibling rather than instead of one.

## Provenance

First-party observation made during the unattended maintenance pass of 2026-08-05, which reproduced the silent `## History` loss on itself. No stored evidence record exists for it, so the source is free text rather than a citation the vault cannot resolve.

## History
- 2026-08-05 merged "Check every section reported dropped arrives with enough to restore it" into this node and deleted its file — Same test, same threshold, same instrument — the original was created minutes earlier in this pass with a fabricated provenance id (`TRANSCRIPT:2026-08-05-unattended-pass`) matching no stored evidence record, which `ost_check` reported as an unresolved-citation violation. `source` is frontmatter with no setter on this surface, so re-creating with truthful free-text provenance and folding the original in is the only available repair. No content changed.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/mcp/mutation-response-dropped-sections-recoverable.test.ts` — No test files found, exiting with code 1
- 2026-09-01 **green** (exit 0) `npx vitest run test/mcp/mutation-response-dropped-sections-recoverable.test.ts` — Duration  1.04s (transform 251ms, setup 0ms, collect 396ms, tests 426ms, environment 0ms, prepare 25ms) [spec 6fd11fc90ca1]

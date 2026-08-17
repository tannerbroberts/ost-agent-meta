---
type: AssumptionTest
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  All three unsupplied sections present and byte-identical after the edit; the
  two supplied sections replaced; no section duplicated; total section count
  unchanged at five.
instrument: npx vitest run test/mcp/edit-node-preserves-unsupplied-sections.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Build a node carrying five `## ` sections — one of them `## History` with more than one dated entry, one of them a reserved section already on the protected list, and one whose body contains a fenced code block with a `## ` line inside it. Call the rewriting tool supplying only two of the five in `prose`. Read the file back.

**Lane: compute-only.** No person is the measurement; a spec file's exit code settles it entirely.

**Why this is red against the repository today, and for the right reason.** This is not a command that fails because a file is missing. The behaviour it asserts is known absent: on 2026-08-05 an unattended pass called `ost_edit_node` on "The same refusal is rediscovered every session, because nothing carries the lesson forward" and its `## History` — four dated entries — was replaced by a single line describing the edit. The three re-parenting records were destroyed. So the `## History` assertion in this spec fails against today's code by direct observation, not by conjecture, and it will go green only once the carry-across rule exists.

The fenced-code-block case and the reserved-section case are in the same spec on purpose: they are the two ways the generalisation could be wrong while the headline case looks fixed. A rule that scans for `## ` naively will treat the line inside the fence as a section boundary; a rule that replaces the hand-listed set rather than subsuming it will regress the three headings that already work.

**What a green run does not settle.** It answers feasibility and nothing else. It says the mechanism can preserve unsupplied sections; it says nothing about whether preserving-by-default is the right default. The cost this solution's body names — that omission now means *keep*, so there is no gesture left that means *remove* — is untouched by this test and is the question a human should weigh separately. It also cannot speak to the retitle case, where a caller renames a section and the rule carries the old one across beside the new; that is a duplicate rather than a loss, it is this assumption's most likely failure mode, and it wants its own test.

## Provenance

First-party observation made during the unattended maintenance pass of 2026-08-05, which reproduced the `## History` loss on itself. There is no stored evidence record for it — the pass observed the defect in the course of its own writing rather than reading it from a channel — so the source is recorded as free text rather than as a citation the vault cannot resolve.

## History
- 2026-08-05 merged "Edit a node holding five sections while supplying two, and check the other three survive intact" into this node and deleted its file — Same test, same threshold, same instrument — the original was created minutes earlier in this pass with a fabricated provenance id (`TRANSCRIPT:2026-08-05-unattended-pass`) that matches no stored evidence record, which `ost_check` correctly reported as an unresolved-citation violation. `source` is frontmatter and no tool on this surface can set it, so re-creating with a truthful free-text provenance and folding the original in is the only available repair. Nothing about the test's content changed.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/mcp/edit-node-preserves-unsupplied-sections.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/mcp/edit-node-preserves-unsupplied-sections.test.ts` — Duration  299ms (transform 64ms, setup 0ms, collect 99ms, tests 6ms, environment 0ms, prepare 26ms)

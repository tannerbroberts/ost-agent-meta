---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  4 of 4 cases hold: (1) the 2026-08-17 verdict wording clears; (2) a
  corroboration line quoting the sibling without a rule name does not clear; (3)
  a line with the rule name but a different sibling does not clear; (4) a
  shared-extent verdict does not clear a later subset-extent flag on the same
  pair. 0 of the 12 real verdict strings from this vault fail case 1.
instrument: npx vitest run test/ost/extent-clear-by-pair.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Temp vault, fixtures, and the twelve verdict strings already written on this vault's nodes (copied into the spec as literals). No person.

**What the spec asserts.** Seed a temp vault with two siblings citing one record, confirm a `shared-extent` flag, then append to the flagged node's `## Issues` a line in the exact shape the 2026-08-17 pass wrote — `2026-08-17 shared-extent flag vs "<sibling>" adjudicated by Torres's interventional test: DISTINCT …` — and assert the flag is gone on the next `computeNextWork`. Negative controls: a line that quotes the sibling inside a corroboration sentence with no rule name must leave the flag; a line with the rule name and a *different* sibling must leave the flag. Drift control: after a verdict clears a `shared-extent` flag, add one more citation beneath one sibling so the relation becomes `subset-extent`, and assert the new flag appears despite the old verdict. Finally, feed all twelve real verdict strings from this vault through the matcher and assert each is recognised.

**Why it is red today, and for a reason specific to this question.** Suppression in `detectHygiene` matches the whole issue string (that is what `test/ost/extent.test.ts` pins and what four passes of prose verdicts failed to match); case 1 fails on today's code because the prose line is not the issue string. Cases 2–4 pass today trivially, which is why case 1 is the one that makes the file red and cases 2–4 are there to keep it honest once a builder loosens the key. **This surface cannot write the spec file, so the command currently fails on `No test files found`, is filed `no-spec`, and grants no permit** — the deliverable is the file with these assertions.

**What a green does NOT settle.** Whether a pass writes "MERGE" in a verdict and never merges; the matcher never reads the verdict's content, so that misuse is invisible to this spec and observable only across firings.

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/extent-clear-by-pair.test.ts` — test/ost/extent-clear-by-pair.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/extent-clear-by-pair.test.ts` — test/ost/extent-clear-by-pair.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/extent-clear-by-pair.test.ts` — test/ost/extent-clear-by-pair.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/extent-clear-by-pair.test.ts` — test/ost/extent-clear-by-pair.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/ost/extent-clear-by-pair.test.ts` — test/ost/extent-clear-by-pair.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/extent-clear-by-pair.test.ts` — test/ost/extent-clear-by-pair.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/ost/extent-clear-by-pair.test.ts` — test/ost/extent-clear-by-pair.test.ts does not exist — no spec was collected, so nothing was measured

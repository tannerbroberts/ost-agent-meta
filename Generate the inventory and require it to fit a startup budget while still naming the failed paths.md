---
type: AssumptionTest
source: 'TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f'
created: '2026-08-06'
evidence: assertion
threshold: >-
  The generated inventory is under 4,000 tokens and contains the parent
  directory of every path that failed in the captured corpus. Both conditions,
  not either — an inventory that fits and does not cover, or covers and does not
  fit, refutes the solution as written.
instrument: npx vitest run test/preflight/workspace-inventory-fits-and-covers.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Generating a listing and counting tokens against a fixed set of paths harvested from the corpus.

**What it does.** Generate the startup inventory for this workspace. Assert its token count is under 4,000. Then extract every path that failed in the transcript corpus and assert the inventory names each one's parent directory — because that is the resolution at which it would actually have helped. Report both numbers on failure, since which condition breaks determines whether the solution narrows or dies.

**Why it is red today.** No inventory generator exists. Missing-file red, and this sweep could not read the product repository to name a better path — `ost_read_repo` is off the unattended surface and a direct source read was refused for permissions.

**Why the bar is where it is.** 4,000 tokens is a judgement, not a measurement, and should be argued with rather than inherited: it is roughly the largest fixed startup cost that still leaves an unattended pass its working context. A human who thinks the real budget is 1,000 or 10,000 should change it before this runs, because the whole verdict turns on it.

**What a green does NOT settle.** That a run given the inventory reads it, or that reading it changes which command it composes. This measures the artefact, not the behaviour, and the behavioural half needs the run's own transcripts after the fact.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/preflight/workspace-inventory-fits-and-covers.test.ts` — No test files found, exiting with code 1

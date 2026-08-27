---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
threshold: >-
  zero of 50 records inserted after the first page is served are unreachable by
  paging to exhaustion
instrument: npx vitest run test/evidence/cursor-skips-late-arrivals.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

Seed a vault past the cap, serve the first page, then capture 50 new evidence records with ids drawn the way the transcript channel actually draws them. Page to exhaustion from the stored cursor and assert every one of the 50 was served at least once.

**The bar is zero, deliberately.** A convention that loses evidence silently is not partially acceptable; one unreachable record is the defect. Fifty is chosen because with random-hex ids the expected loss is about half, so a run that loses none is strong evidence the key is monotonic and a run that loses roughly twenty-five confirms the parent assumption is false on mechanism rather than on chance.

**A refuted verdict here is the useful outcome, and is the likelier one.** This test is written to kill its own solution if the data does not support it. If it fails, the finding is not "build the cursor better" — it is that the borrowed convention's precondition is violated by this queue, and a reader comparing the three candidates under this opportunity should weight it down accordingly.

**Why the command is red today.** `test/evidence/` exists and holds two specs (`age-out-preserves-novel.test.ts`, `corroborate-disposition.test.ts`, listed with repo sight on 2026-08-27); no file by this name is among them, so this is a **no-spec red** — it fails for the reason any unwritten spec would fail, and it hands a builder only the filename plus the assertion stated above. That weakness is forced rather than chosen: the instrument grammar accepts a bare spec path and rejects a `-t` selector as shell punctuation, so behaviour that does not exist yet cannot be named inside a file that does. The sibling test "A second computeNextWork call on an unchanged vault returns capped-list members the first did not" carries the full account.

**What this test does not settle.** Only reachability. It says nothing about page size, nothing about whether cursor state survives a crash between firings, and nothing about desirability, viability or usability — no operator is involved and none is asked.

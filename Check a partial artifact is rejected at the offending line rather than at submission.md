---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  A dialect violation in a partial artifact is reported at its own line, with no
  requirement that the artifact be complete or submittable.
instrument: npx vitest run test/eval/incremental-parse.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: the artifact can be meaningfully checked while incomplete.** A parser that only accepts whole, well-formed input cannot help here — an artifact three lines in is by definition not complete, and if partial input is rejected as malformed rather than checked for dialect, incremental validation has nothing to stand on.

**Risk category: feasibility, and it is the question that decides whether this node is buildable at all.**

**Design.** Feed the parse-only entry point a three-line fragment containing a type annotation. Assert the violation is reported at its own line and that incompleteness is not itself an error. Repeat with the fragment from the observed 172-line rejection truncated at line 24, and assert the same defect is found there.

**Why it is small.** Two fragments, no execution, no live surface.

**What it does NOT cover.** Whether composing actually happens in a way that leaves intermediate state to check. The node names this openly: if artifacts are written whole in a single act, there is no "line three" at which to validate and this reduces to a dry-run before submission — a smaller and different idea. That is a question about the composing surface rather than the target one, and this test looks only at the target.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/eval/incremental-parse.test.ts` — No test files found, exiting with code 1

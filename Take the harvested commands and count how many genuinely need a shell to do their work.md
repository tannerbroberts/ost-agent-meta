---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 70% of commands need no shell feature at all.
instrument: npx vitest run test/runner/shell-necessity-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that most commands do not need a shell. If a lot of real work is genuinely a pipeline, rebuilding composition and redirection above a shell-less exec means reimplementing a shell badly, with its own quoting rules people will get wrong in new ways.

**Risk category: feasibility.**

**Design.** Classify every command in the harvested transcripts: runs as a program and argument list with no shell features at all, needs one shell feature, or needs several. Weight by frequency. The share needing nothing is what a shell-less path would serve directly.

**Why it is small.** Mechanical classification over a corpus that already exists.

**What it will not cover.** It counts commands as written, and a caller who knew a shell-less path was the default would write differently. The pipelines in the corpus are also mostly ad-hoc inspection rather than load-bearing work, which this does not separate.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/shell-necessity-census.test.ts — Classifies each harvested command as needing a shell or expressible as argv, and asserts the argv path executes the latter without a shell; fails today because every command is handed to a shell as a string.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/shell-necessity-census.test.ts` — No test files found, exiting with code 1

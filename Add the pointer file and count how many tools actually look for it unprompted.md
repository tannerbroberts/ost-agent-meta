---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 6 of 10 cold sessions find the vault, and at least 4 do so via the
  pointer file.
instrument: npx vitest run test/config/vault-pointer-resolution.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that something will read it. A pointer nobody is required to look for changes nothing except that the information is technically present.

**Risk category: usability.**

**Design.** Add the file to the project root. Then, over ten cold sessions started in that repository with no mention of a vault, count how many locate the vault and how many of those did so via the file. Do not prompt.

**Why it is small.** The file is three lines. Ten cold starts is an afternoon.

**What it will not cover.** Ten sessions with one agent on one repository. A different agent, or one whose conventions differ, may never look — and the whole value of the approach rests on convention rather than on the file.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/config/vault-pointer-resolution.test.ts — Places the pointer file in a project root and asserts each vault-resolving entry point finds the vault from it with no path argument; fails today because no entry point reads such a file.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/config/vault-pointer-resolution.test.ts` — No test files found, exiting with code 1

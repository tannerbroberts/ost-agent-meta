---
type: AssumptionTest
status: unvalidated
source: 'TRANSCRIPT:6e66c934-24d8-4200-b6f2-7af23002c478'
created: '2026-08-06'
evidence: observed
threshold: >-
  Both titles traverse all four routes with correct quoting or explicit refusal,
  and no call path yields the unwrapped string without naming a destination.
instrument: npx vitest run test/security/tainted-argument-guard.test.ts
---
#AssumptionTest #unvalidated #evidence/observed

**Lane: compute-only.** Whether a value arrives at a command still carrying its origin is decided by running it there.

Use the two titles that actually broke — the one beginning `{Charge` and the one containing `*{threshold`, both real nodes in this vault — and push them from frontmatter through every route by which a string reaches a command: a search over node text, a path built for a file read, a message formatted for output, and a comparison against a literal. Require that each route either quotes correctly for its destination or refuses, and that no route produces a bare interpolated string.

Then the part that separates the two possible designs. Assert there is no way to obtain the plain string except through a call that names a destination. If a bare form can be had — for a log line, for an equality check — the scheme is a convention and the parent assumption is false, because the hole will be found eventually by a title nobody anticipated. A guard with an escape hatch is worse than no guard, since the visible parse error is replaced by a silent belief in coverage.

**Pre-committed bar:** both titles traverse all four routes with correct quoting or an explicit refusal, and no call path yields the unwrapped string without naming a destination. Any bare form available anywhere fails this, however convenient its use.

**What a green run here does not settle.** It covers routes that exist today. A route added next month inherits nothing from this spec unless the bare form is genuinely absent, which is why the second half of the bar matters more than the first. It also says nothing about whether the wrapping is worth its cost in ergonomics — a scheme that is correct and unpleasant enough to be worked around has failed in a way no exit code reports, and that judgement needs someone who has written code against it.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/security/tainted-argument-guard.test.ts` — No test files found, exiting with code 1

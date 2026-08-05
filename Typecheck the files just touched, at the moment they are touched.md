---
type: Solution
source: 'TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd'
created: '2026-08-04'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A narrow check catches the same diagnostic far faster than the whole-project run]]

Keep the check but move it. Instead of one whole-project `tsc --noEmit` at the end of a batch, run a narrow check over the file that just changed and its immediate dependents, and return the diagnostic attached to the edit that caused it.

**Shape.** A per-edit hook. The verdict is advisory text handed back with the edit result, not a refusal — a run mid-refactor is legitimately broken between two edits, and a gate that forbids that would make ordinary work impossible.

**Why this one is the strongest candidate and also the riskiest.** It is the only option here that catches the class *and* attributes it: the diagnostic arrives naming the edit, so the run cannot mistake it for a pre-existing problem. The risk is entirely cost. `tsc` on a single file in a project with this repo's type graph is not obviously fast, and a check that adds seconds to every edit will be turned off within a week — which is worse than not building it, because the tree will record it as tried.

**Against the alternatives.** Strictly more expensive than the symbol manifest and strictly more reliable. Compared with declared-intent, it needs no cooperation from the run at all, which matters because the two captured failures were both cases where the run did not know it was making a mistake.

**Deliberately out of scope.** This does not attempt to catch anything a typechecker cannot see. `b7aae32d`'s readonly-assignment error is in scope; a logic error that compiles is not, and nothing here should be read as claiming otherwise.

## Test

"Time a single-file check against the whole-project run it would replace"

`npx vitest run test/runner/incremental-typecheck.test.ts`

Green when the single-file check finds the known TS2339 in under 2s and beats the whole-project run by a wide margin on the same machine. It settles cost and detection; it does not settle the mid-refactor false-positive rate, which is what would actually make this unbearable.

## History
- 2026-08-05 unlinked "Time a single-file check against the whole-project run it would replace" — moved under "A narrow check catches the same diagnostic far faster than the whole-project run" — the belief this test measures now has a node of its own

---
type: Solution
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Few enough consumers read a suite result as a boolean that they can all be migrated at once]]

A suite result is not a boolean. It carries the set of things it did not run — excluded, skipped, quarantined, never collected — and any reader that treats it as a verdict has to look at that set. A gate reading a green with a non-empty exclusion set refuses to call it full coverage.

**This is the invisibility half of the need, and it is the half that does the damage.** A manual exclusion costs the operator some retyping. A green that overstates its own coverage costs whoever reads it next, which on this project is frequently a gate, a later pass, or a person deciding something is safe to build on.

**The shape is already in this vault, one layer up.** "A result must state what it did not cover" is exactly this principle applied to assumption-test results, and it shipped. This candidate is the same idea pointed at suite results instead — which is a genuine argument in its favour, because the principle has already survived contact once here, and also an argument for checking whether the two should share a mechanism rather than being built twice.

**Where it is stronger than its siblings.** The quarantine-list and expiry candidates both assume the exclusion is *declared*. This one also catches the undeclared cases: a test file that failed to collect, a suite that exited early, a filter typo that silently matched nothing. Those produce a green that covered less than it claims with nobody having decided anything, and no amount of quarantine hygiene sees them.

**The cost, which is not small.** Every consumer of a suite result has to be taught to read the new shape, and the ones that are not taught keep reading the boolean and are now *more* wrong, because the exclusion set exists and they are ignoring it. A partial rollout of this is worse than none. That migration cost is the thing to size before building — and this vault has felt it before, under "When the rules tighten, my existing tree is stranded out of compliance".

_Agent-ideated, unvalidated — one of three competing candidates under this opportunity, for a human to compare rather than adopt._

## Definition of done

"Census every consumer that reads a suite result as a pass-or-fail boolean"

```
npx vitest run test/runner/suite-result-consumer-census.test.ts
```

Red today: nothing enumerates the consumers of a suite verdict, so the migration is unsized. Green when at most five consumers exist and each can be migrated in a single change.

**Why this before anything is built.** A partial rollout of this candidate is worse than no rollout — an untaught consumer keeps reading the boolean while an exclusion set exists beside it, and is now confidently wrong rather than merely uninformed.

**What this does not settle.** It counts consumers, not the cases they would newly catch. This candidate's strongest argument is that it also surfaces *undeclared* shortfalls — a file that failed to collect, a filter typo matching nothing, a suite exiting early — and none of those appear in a consumer census. That upside needs its own replay over past runs.

## History
- 2026-08-05 unlinked "Census every consumer that reads a suite result as a pass-or-fail boolean" — moved under "Few enough consumers read a suite result as a boolean that they can all be migrated at once" — the belief this test measures now has a node of its own

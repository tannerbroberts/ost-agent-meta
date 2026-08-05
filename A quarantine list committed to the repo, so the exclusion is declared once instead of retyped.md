---
type: Solution
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Enough distinct files get hand-excluded that declaring them once beats retyping]]

The known-flaky files live in a file in the repository, with a reason and a date beside each. The runner reads it. Nobody retypes `--exclude` into an invocation again.

**This candidate targets the first half of the need — the exclusion being manual — and only incidentally the second.** Its siblings take the other halves: [[A result carries its own exclusion set, so a gate cannot read it as full coverage]] attacks the invisibility, and [[Quarantine entries expire, so a workaround cannot become permanent by inattention]] attacks the permanence. They compose, which means the comparison a human should make is not "which one" but "which one first, and does it stand alone".

**Why declaring once matters more than the typing it saves.** A hand-typed exclusion is invisible to everyone except the person who typed it: it exists only in one shell invocation in one session. Moving it into the repository converts a private workaround into a shared fact — reviewable, greppable, and attributable. In the captured session the same exclusion was typed three times by the same run within minutes; had it been typed twice with different spellings, or omitted once, nothing would have noticed.

**The objection worth taking seriously.** A committed quarantine list is a place where tests go to die quietly. It lowers the cost of not fixing a flaky test, which is precisely why the expiry sibling exists — and it is a fair reading that this candidate is *harmful* without it, because it makes the bad state comfortable. A human comparing these should probably treat this and expiry as one candidate rather than two.

**Prior art in this vault.** The flake-attribution work under [[A test that failed because the machine was busy looks exactly like one that failed because I broke something]] is upstream: perfect attribution would reduce how often anything needs quarantining at all, but would not eliminate it, since a test can be correctly identified as flaky and still need to not block the run today.

_Agent-ideated, unvalidated — one of three competing candidates under this opportunity, for a human to compare rather than adopt._

## Definition of done

[[Count the distinct test files ever hand-excluded across the captured sessions]]

```
npx vitest run test/telemetry/hand-exclusion-census.test.ts
```

Red today: nothing extracts exclusion flags from the harvested invocations, so the distinct count does not exist. Green when at least three distinct test files are shown to have been hand-excluded across the captured sessions.

**A red here is a live possibility, not a formality.** The record is known to contain one such file, excluded three times within a single session. If the census finds only that one, the honest answer is to fix the flake and build nothing — which is the result this test is written to be able to produce.

**What this does not settle.** The candidate's real hazard, that a comfortable quarantine lowers the cost of never fixing anything. That is why [[Quarantine entries expire, so a workaround cannot become permanent by inattention]] may be a precondition for this rather than an alternative to it.

## History
- 2026-08-05 unlinked [[Count the distinct test files ever hand-excluded across the captured sessions]] — moved under [[Enough distinct files get hand-excluded that declaring them once beats retyping]] — the belief this test measures now has a node of its own

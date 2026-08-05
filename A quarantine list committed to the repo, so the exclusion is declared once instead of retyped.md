---
type: Solution
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

The known-flaky files live in a file in the repository, with a reason and a date beside each. The runner reads it. Nobody retypes `--exclude` into an invocation again.

**This candidate targets the first half of the need — the exclusion being manual — and only incidentally the second.** Its siblings take the other halves: [[A result carries its own exclusion set, so a gate cannot read it as full coverage]] attacks the invisibility, and [[Quarantine entries expire, so a workaround cannot become permanent by inattention]] attacks the permanence. They compose, which means the comparison a human should make is not "which one" but "which one first, and does it stand alone".

**Why declaring once matters more than the typing it saves.** A hand-typed exclusion is invisible to everyone except the person who typed it: it exists only in one shell invocation in one session. Moving it into the repository converts a private workaround into a shared fact — reviewable, greppable, and attributable. In the captured session the same exclusion was typed three times by the same run within minutes; had it been typed twice with different spellings, or omitted once, nothing would have noticed.

**The objection worth taking seriously.** A committed quarantine list is a place where tests go to die quietly. It lowers the cost of not fixing a flaky test, which is precisely why the expiry sibling exists — and it is a fair reading that this candidate is *harmful* without it, because it makes the bad state comfortable. A human comparing these should probably treat this and expiry as one candidate rather than two.

**Prior art in this vault.** The flake-attribution work under [[A test that failed because the machine was busy looks exactly like one that failed because I broke something]] is upstream: perfect attribution would reduce how often anything needs quarantining at all, but would not eliminate it, since a test can be correctly identified as flaky and still need to not block the run today.

_Agent-ideated, unvalidated — one of three competing candidates under this opportunity, for a human to compare rather than adopt._

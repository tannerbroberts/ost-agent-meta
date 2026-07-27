---
type: Solution
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion
[[Does a stated denominator catch a drop nobody predicted]]

**The idea.** Any tool that reports "N found" also reports "over M examined, K unreadable". The operator reads a ratio, never a bare integer.

**Why this one first.** It is the smallest change that makes the failure *visible without being anticipated*. The em-dash bug was not on anyone's list; a denominator would have shown 302 of 306 entries examined and 4 files unreadable without anyone having thought about filename quoting in advance. Guards catch the failures you predicted. A denominator catches the ones you did not.

**Where it fails.** A denominator computed by the same broken traversal is just as wrong — if the walker never enumerates the em-dashed file at all, M excludes it and the ratio reads 100%. This only works when the denominator comes from a DIFFERENT source than the counter (directory listing vs. git, say), which is more than a print statement and is the real cost of the idea.

⚠️ Unvalidated. Agent-ideated from an observed failure.

## Issues
- 2026-07-27 Not built this pass, 2026-07-27 (thirteenth). It was the briefing's ranked first candidate and it was passed over deliberately, so the next pass does not read the silence as an oversight. A defect surfaced during real use -- `loop step` recording exit 0 for a command that never ran -- outranked it on two counts: it was `observed` rather than reasoned, in a tree where 227 of 238 nodes rest on `assertion`, and it sat in the health record every other claim this loop makes depends on. The condition the eleventh pass attached still stands unchanged and unmet: build it with the denominator from an INDEPENDENT source, or do not build it.
- 2026-07-27 SHIPPED 2026-07-27 (fourteenth pass) as ost-agent v0.22.0, commit df5288a, registry-confirmed. Built on the third ranking after two deliberate deferrals, per the standing 'a third deferral should either build it or kill it' condition. The condition the eleventh pass attached -- build it with the denominator from an INDEPENDENT source or do not build it -- was met and is the part that took the work: `readTreeCensus()` reports examined/dropped/unreadable from the SAME walk that produces the nodes (the only thing that knows the counter skipped something is the counter), and `reconcileWithGit()` takes a second denominator from `git ls-files -z`, an index maintained by another program through another code path. Both were needed: same-walk accounting cannot see a file the walk never enumerated, which is precisely this node's stated failure mode. Verified against a real vault, not only fixtures -- a planted typo'd `type` was named as dropped, and a file present in git but absent from disk was named as unseen by the walk. `-z` is load-bearing and has a recorded positive control: with it removed the em-dash filename test fails. Follow-on test: [[Does a stated denominator catch a drop nobody predicted]].

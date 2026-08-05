---
type: Solution
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion
[[A stated denominator makes a reader notice a drop they would otherwise have missed]]

**The idea.** Any tool that reports "N found" also reports "over M examined, K unreadable". The operator reads a ratio, never a bare integer.

**Why this one first.** It is the smallest change that makes the failure *visible without being anticipated*. The em-dash bug was not on anyone's list; a denominator would have shown 302 of 306 entries examined and 4 files unreadable without anyone having thought about filename quoting in advance. Guards catch the failures you predicted. A denominator catches the ones you did not.

**Where it fails.** A denominator computed by the same broken traversal is just as wrong — if the walker never enumerates the em-dashed file at all, M excludes it and the ratio reads 100%. This only works when the denominator comes from a DIFFERENT source than the counter (directory listing vs. git, say), which is more than a print statement and is the real cost of the idea.

⚠️ Unvalidated. Agent-ideated from an observed failure.

## Issues
- 2026-07-27 Not built this pass, 2026-07-27 (thirteenth). It was the briefing's ranked first candidate and it was passed over deliberately, so the next pass does not read the silence as an oversight. A defect surfaced during real use -- `loop step` recording exit 0 for a command that never ran -- outranked it on two counts: it was `observed` rather than reasoned, in a tree where 227 of 238 nodes rest on `assertion`, and it sat in the health record every other claim this loop makes depends on. The condition the eleventh pass attached still stands unchanged and unmet: build it with the denominator from an INDEPENDENT source, or do not build it.
- 2026-07-27 SHIPPED 2026-07-27 (fourteenth pass) as ost-agent v0.22.0, commit df5288a, registry-confirmed. Built on the third ranking after two deliberate deferrals, per the standing 'a third deferral should either build it or kill it' condition. The condition the eleventh pass attached -- build it with the denominator from an INDEPENDENT source or do not build it -- was met and is the part that took the work: `readTreeCensus()` reports examined/dropped/unreadable from the SAME walk that produces the nodes (the only thing that knows the counter skipped something is the counter), and `reconcileWithGit()` takes a second denominator from `git ls-files -z`, an index maintained by another program through another code path. Both were needed: same-walk accounting cannot see a file the walk never enumerated, which is precisely this node's stated failure mode. Verified against a real vault, not only fixtures -- a planted typo'd `type` was named as dropped, and a file present in git but absent from disk was named as unseen by the walk. `-z` is load-bearing and has a recorded positive control: with it removed the em-dash filename test fails. Follow-on test: "Does a stated denominator catch a drop nobody predicted".
- 2026-08-05 2026-08-05 Left un-instrumented because it shipped, and recorded here so a later pass does not read the gap as an oversight. The 2026-07-27 issue above states this went out as v0.22.0 (`df5288a`, registry-confirmed) with the eleventh pass's condition met — `readTreeCensus()` reporting examined/dropped/unreadable from the same walk that produces the nodes, and `reconcileWithGit()` taking a second denominator from `git ls-files -z`, an index maintained by another program through another code path. Both halves were required precisely because same-walk accounting cannot see a file the walk never enumerated, which is this node's own stated failure mode. Any instrument I wrote for that behaviour would pass on arrival, and a command that cannot fail measures nothing. This is now the fourth node in this sweep parked for shipped-or-abandoned behaviour rather than for lack of a testable claim — alongside "A result must state what it did not cover", "Believability ladder required on every node" and "Append-only tool surface with no delete or shell tool". Worth a human's attention as a pattern rather than four separate notes: `solutionsMissingInstruments` cannot distinguish a solution nobody has made runnable from one whose behaviour already ships and therefore must not be, so the count reads as 124 outstanding items when some fraction of it is correctly finished work. A `shipped`-aware exclusion, or a recorded reason-for-no-instrument that the sweep honours, would stop every future pass re-deriving these four judgements from scratch. The live follow-on here is untouched and remains the real question: "Does a stated denominator catch a drop nobody predicted" asks whether the ratio surfaces a failure nobody anticipated, and the em-dash bug it was built from was found by accident rather than by the mechanism.

## Definition of done

The behaviour this node describes shipped in v0.22.0 (`df5288a`), so the buildable work here is no longer the denominator itself — it is the record the follow-on test is counted over.

"Does a stated denominator catch a drop nobody predicted"

```
npx vitest run test/ost/census-drop-history.test.ts
```

## History
- 2026-08-05 unlinked "Does a stated denominator catch a drop nobody predicted" — moved under "A stated denominator makes a reader notice a drop they would otherwise have missed" — the belief this test measures now has a node of its own

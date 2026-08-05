---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A tree version can be computed cheaply and still detect every change]]

Each sweep carries a version derived from the tree's state. A caller holding a sweep may ask whether it is still current by presenting that version; if nothing has changed, the answer is a few bytes rather than the whole outstanding list. The caller keeps re-asking exactly as often as it likes, and the cost of doing so collapses.

This treats the behaviour as reasonable rather than wrong. A pass that re-reads after a batch of writes is being careful, and the fix is to make carefulness cheap instead of asking it to be less careful.

**Compared to the alternatives.** Requires nothing of the caller beyond holding one string, and it preserves the confirmation the re-reads were there to provide. It does not reduce the number of calls at all — the trace would look identical — so if the concern is call count rather than tokens, this changes nothing visible.

**What would make this the wrong pick.** Computing a version that is cheap and honest is the whole difficulty. If deriving it costs as much as producing the sweep, nothing is saved; if it is cheap but coarse, a caller will be told it is current when it is not, which is worse than re-reading.

## Definition of done

[[Time a candidate version computation against producing the full sweep]]

```
npx vitest run test/ost/sweep-version-cost.test.ts
```

Red today because the sweep returns no version at all — `ost_next_work` recomputes the outstanding list from scratch on every call and hands the caller nothing to compare against, so there is no cheap candidate to time and no change-detection to score. Green means both candidate versions (mtime-based and content-hash-based) cost under 10% of producing the sweep on this vault, and each detects all twenty representative changes.

This is the command that decides whether the solution is worth building at all, rather than one that confirms it after the fact. A version that is cheap and coarse is worse than the re-reading it replaces: it tells a caller the tree is current when it is not.

What it does not settle: one vault at one size. The cheap candidate's cost may grow differently from the sweep's as the tree gets larger, so the ratio is the finding and neither absolute number is.

## History
- 2026-08-05 unlinked [[Time a candidate version computation against producing the full sweep]] — moved under [[A tree version can be computed cheaply and still detect every change]] — the belief this test measures now has a node of its own

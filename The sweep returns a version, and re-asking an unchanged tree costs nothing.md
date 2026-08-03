---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Each sweep carries a version derived from the tree's state. A caller holding a sweep may ask whether it is still current by presenting that version; if nothing has changed, the answer is a few bytes rather than the whole outstanding list. The caller keeps re-asking exactly as often as it likes, and the cost of doing so collapses.

This treats the behaviour as reasonable rather than wrong. A pass that re-reads after a batch of writes is being careful, and the fix is to make carefulness cheap instead of asking it to be less careful.

**Compared to the alternatives.** Requires nothing of the caller beyond holding one string, and it preserves the confirmation the re-reads were there to provide. It does not reduce the number of calls at all — the trace would look identical — so if the concern is call count rather than tokens, this changes nothing visible.

**What would make this the wrong pick.** Computing a version that is cheap and honest is the whole difficulty. If deriving it costs as much as producing the sweep, nothing is saved; if it is cheap but coarse, a caller will be told it is current when it is not, which is worse than re-reading.

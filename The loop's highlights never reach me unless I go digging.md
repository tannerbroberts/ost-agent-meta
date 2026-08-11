---
type: Opportunity
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
created: '2026-08-11'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Announce a red-to-green flip on the founder's channel the moment it is observed]]
[[A highlights digest distilled from what vault history already records]]
[[A highlight criteria note the founder edits and the loop reads before deciding what to surface]]

**The need (founder's voice, 2026-08-11, verbatim in substance):** "If a red test goes green, I'm not notified. If a long-standing opportunity gets killed, I'm not made aware of the reasons... I'd like to be at least notified of the highlights, but I haven't found a good way to helping you determine what's worth sharing, nor am I certain that the highlights are happening as hoped." And the success criterion behind it: "I want this whole build + discover loop to be a compute success, not my success... the thesis gets proven if it can succeed on its own."

**What the record shows against it (observed counts from the same session):** 20 post-build red-to-green observations and 4 was-already-green records sit in vault history and none was ever surfaced as a highlight. Per-firing reports exist but carry one paragraph per firing, not milestones. No opportunity has ever been killed, because kill/promote is human-only today — so half the highlight classes the founder wants notification for are events the current doctrine cannot produce without him, a boundary any solution here must respect rather than quietly relax.

**The trust cost, observed the same night:** the build loop reported "NOT MERGED" on PRs #94 and #95 while GitHub showed both merged in the same minute, and eight PRs (#88–#95) sat merged while the founder said "I don't get much reassurance that the build loop is building anything." A false failure report is the inverse of a highlight, and it burned exactly the trust that surfaced highlights would have built.

**Litmus — more than one way to address this:** yes. Announce each transition the moment it is observed; distill a per-firing or periodic digest from what history already records; let the founder curate what counts as a highlight in a durable artifact the loop reads; keep a milestone ledger a human reads at their own cadence. Passes.

**Distinctness.** The parent category holds the pull-side pain — finding out anything means digging through files. This node is the push side: the milestones themselves should announce their occurrence. It is also distinct from "A block stops everything and announces itself to no one", which is about waits and blocks; this is about wins and verdicts.

**Provenance caveat:** the note is founder first-person in substance, but it arrived on the inbox channel, which has earned `assertion` — so this node declares `assertion` until a test or a human moves it. The counts say highlights exist unsurfaced; only the founder can say which of them he would have wanted.

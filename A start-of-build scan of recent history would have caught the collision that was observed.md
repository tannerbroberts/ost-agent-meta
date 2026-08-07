---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** At 00:47Z the second pass cloned the repo clean, and the first pass's commit did not land until 02:56Z. So the scan this solution proposes would have found nothing at the moment the pass started — the prior art did not exist yet.

That is the sharp form of the doubt and it is why this assumption is worth testing rather than assuming: the candidate is only useful if the scan runs at a moment when the other pass's work is already visible, which means it must run repeatedly during the build, not once at the start. Stated as it could be false: **a single scan at start-of-build would not have caught the one collision on record.**

If that is right, this solution is not wrong but is mis-specified, and its honest form is a scan on a cadence — which moves it much closer to its early-push sibling and weakens the claim that it is a distinct approach.

**What would make it true anyway.** The window matters. Most duplicated work in this loop is not started within two hours of its twin; if the typical gap is a day, a start-of-build scan catches most of it and the observed case is the unlucky tail. Nobody has counted, and this tree holds exactly one collision.

⚠️ Unvalidated, agent-authored, n=1.

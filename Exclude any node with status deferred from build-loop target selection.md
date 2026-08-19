---
type: Solution
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Add `status !== 'deferred'` as a hard filter in whatever query the build loop runs to pick its next target, alongside whatever "has an instrument, cleared its permit" filter it already applies. Cheapest possible fix if the loop is simply not checking status at all — a one-line predicate change.

**What would make this the wrong pick.** If the loop already filters on status and the real bug is that it's reading a stale snapshot of the node (a caching issue), this fix does nothing: the stale copy would still report `status: unvalidated` or whatever it was cached as before the human deferred it. Worth checking which is true before building this.

⚠️ Unvalidated. Proposed by an unattended pass reasoning from three observed build-loop reports; no repo sight available this pass to confirm which failure mode is actually present.

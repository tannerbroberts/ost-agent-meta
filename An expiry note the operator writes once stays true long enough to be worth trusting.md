---
type: Assumption
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: viability.**

The belief, stated so it could turn out false: a sentence the operator writes once about what an expiry means on this machine remains accurate long enough that a future session is right to act on it.

**Why this is the risky half and the feasibility half is not.** Read with repo sight on 2026-08-29, `ost.config.yaml` already carries several hand-edited operator fields that the tooling reads and never writes — `discovery.target`, `evidence.ageOutDays`, `adapters.*.enabled`, `product.repos`, `web.lookupBudget`. Adding one more field that is merely printed back needs no new mechanism, so there is nothing to test there. Recorded explicitly so a later pass does not spend an ask discovering it.

**Why it could be false.** The note encodes a fact about a moving target — how long this suite takes on this machine. Suites grow, machines change, and a note saying "6-9 minutes, do not re-wait" keeps being printed with full confidence after it stops being true. That is worse than the present silence: today an expiry confuses a session, whereas a stale note confidently sends it the wrong way. This project's own tree already records that artifacts requiring recurring founder input are the ones that go unmaintained, and carries a live assumption on exactly that pattern about a highlight criteria note.

**What would make it true anyway.** If the note is written at the right altitude — about the *shape* of the answer ("suite waits belong in the background, not in an `await`") rather than a duration — it may survive changes that a numeric claim would not. Whether an operator writing such a note naturally reaches for the durable phrasing or the brittle one is part of what a test here has to observe, not assume.

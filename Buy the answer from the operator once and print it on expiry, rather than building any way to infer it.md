---
type: Solution
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[An expiry note the operator writes once stays true long enough to be worth trusting]]

**Variation dimension: bought-vs-built. Position taken: nothing is built here; the missing knowledge is bought from the person once and replayed forever.**

The operator records, once, in the same hand-edited config that already carries `discovery.target`, what an expiry on this machine means and what to do about it — for example: "the full suite takes 6-9 minutes here; if a wait on it expires at 300s, do not re-wait, start it in the background and come back." On expiry the helper prints that sentence verbatim next to the condition that failed. No gradient is computed, no state is kept between calls, no cooperation is asked of the subject process.

**Why buying beats building for this particular gap.** The thing the expired session actually lacked was not telemetry — it was local knowledge that a full suite on this machine outruns a 300s ceiling. That knowledge already exists, in one head, and is stable for months. Every other candidate spends engineering to re-derive at runtime something a person could have written down in one line. This position takes the founder's own recorded preference for hand-edited operator files — the same shape as `discovery.target` and `evidence.ageOutDays` — and extends it one field.

**Against its siblings.** It is by far the cheapest and the only one that works identically for local, remote and queued subjects, because it makes no observation at all. It is also the only one that cannot adapt: it says the same sentence on the first expiry and the fifth, so it does not fix the re-issue loop, only makes each expiry less confusing. The heartbeat and budget-escalation candidates both act; this one only informs.

**What would make this the wrong pick, stated plainly.** It is a recurring-input artifact, and this project's own tree already records that such artifacts are the ones that go unmaintained — there is a live assumption elsewhere on exactly that question, about a highlight criteria note. A stale expiry note fails in the dangerous direction: it confidently tells a future session to do the wrong thing, which is worse than the current silence. It is the right pick only if the note is short enough to stay true across machine and suite changes.

**No instrument, and the reason differs from its siblings'.** The other two candidates are unreachable because the helper is not in this repository. This one is unreachable because its load-bearing claim is about whether one person writes and maintains one sentence — a viability question about a human, not about code. Either way there is no spec in this product's `test/` that could go red for it.

Unvalidated. Agent-ideated on 2026-08-29; a human to review.

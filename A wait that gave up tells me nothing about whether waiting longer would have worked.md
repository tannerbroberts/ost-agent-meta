---
type: Opportunity
source: 'TRANSCRIPT:8910f58f-ee8e-443a-84c9-a9eaf1d18b8f'
created: '2026-08-29'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed

**The need, from the running agent's side:** "My wait gave up. I cannot tell from that whether the thing I was waiting for was one second away or would never finish, so the only move I have is to wait again — and I did, four times, unattended, for nothing."

**What was observed (mechanical, 2026-08-29).** Session `8910f58f` recorded five consecutive `await: gave up after 300s; the condition still exits 1.` events while waiting on a full test-suite run, with two identical re-issues of the same command in between. The caller had stated a longer budget on the invoking tool — `{"command":"await 'grep -q \"Test Files\" /tmp/suite-branch.txt'","timeout":400000}` — and the helper expired at its own 300s ceiling regardless. Roughly twenty minutes of unattended wall clock produced no information about the subject being waited on.

**The need is about what an expiry says, not about how long it is.** Lengthening the ceiling would have changed this run's outcome and not the need: whatever the ceiling, the expiry message carries no gradient. It does not say how close the condition got, whether it was trending toward true, or whether the subject process is still alive at all. Absent that, an identical retry is the rational move, which is exactly what makes the failure repeat.

**Litmus test (more than one way to address this?):** Yes — an expiry that reports the condition's last observed state and how it changed across polls; a wait whose budget escalates on re-invocation rather than resetting; a wait that reports the *subject's* liveness alongside the condition's; a caller-side rule that refuses a second identical wait and demands a changed budget or a different condition. Four different shapes, so this is a need rather than a solution wearing a need's grammar.

**How this differs from the siblings already on the tree.**
- "A budget that fails to reach the shim announces itself instead of silently reverting to the constant" is about a budget that is *missing or malformed*. Here a budget was stated, in a channel the helper does not read, and the two disagreed silently — but even if that were fixed, this need would remain.
- "A never-true condition exits with the reserved expiry status while a condition failing on its own merits keeps its own" separates *which kind* of failure occurred. This node is about what a caller should do *after* a legitimate expiry. A reserved exit status addresses the first and not the second; a wait that escalates its own budget addresses the second and not the first. Torres's test passes in both directions.

**Provenance caveat.** This is the agent's own usage of this product, captured mechanically from a session transcript. It grounds usability, not desirability, and must not be read as outside evidence that anyone wants this fixed. Rung `observed` because the provenance is itself a recording, not because anyone corroborated it.

**Not yet ideated.** No solutions hang here. The wait helper is not in this repository — it is on the session's PATH, supplied by the harness — so whether any of the four shapes above is even reachable from here is an open question for an attended pass with the helper's source in view.

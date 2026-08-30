---
type: Assumption
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Count the recorded expiries that later succeeded against those whose condition could never have become true]]

**Risk category: viability.**

The belief, stated so it could turn out false: among the waits that actually expire in this loop, the ones that would have succeeded given more time outnumber the ones that were never going to succeed.

**Why the direction matters more than the mechanism.** Automatic escalation is patience made cheap. If most expiries are genuinely-slow subjects, cheap patience is exactly right and the candidate turns a 300s dead end into a 600s success. If most expiries are never-true conditions — a typo in the grep, a file the subject never writes, a job that died at second three — then the candidate spends up to 2100s of unattended wall clock where today it spends 300s, and it makes the problem it was built for strictly worse. The candidate's own prose names this as the thing that decides it; this node is that thing.

**What makes it genuinely uncertain rather than obvious.** The one recorded instance cuts against the candidate: in `TRANSCRIPT:8910f58f` the condition was `grep -q "Test Files" /tmp/suite-branch.txt`, and it failed five times over roughly twenty minutes. Whether the suite was slow or the redirect never landed is not recoverable from the record — which is itself the parent opportunity's point — so even the one case on hand does not settle the direction.

**Not the only belief beneath that solution.** It also assumes two different waits on the same condition string can safely be treated as one wait retried. That identity question is named in the solution's prose and is not carried here.

## A second recorded instance, and this one is resolvable — it cuts toward "genuinely slow" (2026-08-30)

The body above rests the uncertainty on a single case and says why that case cannot settle it: in `TRANSCRIPT:8910f58f` the condition failed five times over twenty minutes and "whether the suite was slow or the redirect never landed is not recoverable from the record." A second instance is now on record, and the reason it is worth appending is not that it adds a tally — it is that **this record contains the discriminator the first one lacked.**

**The record.** `TRANSCRIPT:f7416208-8bca-41f3-bae1-725cb629da48`, mirrored 0d ago, 12 friction events (4 `tool_error`, 8 `retry`). Five of the retries are `await` waits on test-suite output files: `grep -q "Test Files" /tmp/ostprobe/full-run-2.txt`, `grep -q DONE /tmp/ostprobe/isolated.txt`, `grep -q "Test Files" /tmp/ostprobe/full-run-3.txt` (twice, byte-identical), and `grep -q "Test Files" /tmp/ostprobe/full-run-5.txt` — each with `timeout 600000`.

**Why this one separates slow from never-true.** Between the waits, the same session issued progress checks that read the very files it was waiting on: `grep -cE "^ ✓ test/" /tmp/ostprobe/full-run-3.txt` and `grep -E "^ ❯ test/" /tmp/ostprobe/full-run-5.txt | wc -l`. Those calls are reading *partial* suite output from files that were being written while the wait was expiring. A never-true condition of the kind the body worries about — a typo in the grep, a redirect that never landed, a job that died at second three — produces an empty or absent file and no partial progress to count. Partial output on the waited-for path is positive evidence that the redirect landed and the subject was alive and working; the condition simply had not been reached yet. That is the distinguishing observation `8910f58f` did not contain.

**The mechanism, in the same record.** One `tool_error` reads `Exit code 143 Command timed out after 10m 0s` next to `18:20 up 42 days, 9:17, 3 users, load averages: 22.81 18.64 13.25`. A load average of 22.81 is a saturated machine, which is precisely the condition under which a subject is genuinely slow rather than dead. The session also set its Bash timeout to 600000ms and lost the run to SIGTERM at exactly the ten-minute harness ceiling — so the wait budget and the harness's own kill ceiling were in play in the same run, uncoordinated.

**What this changes, stated narrowly.** The direction of this assumption now has one resolvable instance behind it and it points *toward* the belief being true: expiries here were slow subjects on a loaded box, not conditions that could never come true. It does not make the belief safe. n is 2 sessions, one of which is still unresolvable, both from this vault's own firings and both about the same subject — a vitest suite — which is exactly the workload most likely to be merely slow. A queue that never gets serviced or a grep with a typo would look nothing like this, and neither is represented in the corpus.

**A cheaper route to the pending count, which is the reusable part.** The linked test asks someone to classify recorded expiries as slow-versus-never-true, and the body's objection is that expiry lines are byte-identical. This record shows they are not the only artifact available: **a wait whose file shows partial progress on an interleaved read is classifiable from the transcript alone.** Whoever runs that count should look for reads against the waited-for path in the same session rather than at the expiry lines, which converts a judgement call into a mechanical scan over the existing corpus for some fraction of the cases.

_Source: `TRANSCRIPT:f7416208-8bca-41f3-bae1-725cb629da48`, read in full this pass via ost_next_work. Observed behaviour of this vault's own unattended firing — it grounds usability, not desirability, and is not outside demand data. No test was run and no result is recorded; this node's rung is unchanged at `assertion`._

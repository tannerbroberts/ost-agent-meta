---
type: Solution
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A subject's own progress line is enough to tell a slow run from a stuck one]]

**Variation dimension: who-does-the-work. Position taken: the subject carries it, not the waiter.**

The waiter stops trying to infer anything. Instead the long-running command is started in a form that emits a cheap heartbeat — a line appended to its own output on each unit of progress — and the wait tails that alongside its condition. On expiry it does not say "the condition still exits 1"; it says what the subject last reported and when, so the caller reads "suite: 340 of 512 files, last line 6s ago" and knows the answer is to wait, or reads "last line 280s ago" and knows the answer is not to.

**Why put the work on the subject.** The waiter genuinely cannot know how close a condition is — a `grep -q` is a boolean and has no gradient to report. Only the process being waited on knows whether it is advancing. Every scheme that keeps the work on the waiter is trying to reconstruct, from outside, information that exists in plain text one process over.

**Against its siblings.** The budget-escalation candidate makes a repeat cheaper but still tells the caller nothing about *why* to repeat; this one makes the first expiry informative and may remove the need for a second wait entirely. The operator-recorded-instruction candidate answers the question once, in advance, for all conditions; this one answers it per run, from live state, and costs a change at every call site that starts a long job.

**What it costs, and what would make it the wrong pick.** Every long-running command has to be launched in the heartbeat-emitting form, which is a discipline no mechanism enforces — a job started the ordinary way expires exactly as uninformatively as today, so the failure mode is partial adoption that looks like coverage. It is also the wrong pick where the subject is not a process this side controls: a remote CI run or a queued job has no local output to tail, and those are a large share of the things worth waiting on.

**Where the mechanism would live is an open question.** The `await` helper is on the session's PATH, supplied by the harness, not in this repository. No spec in this product's `test/` can reach it, so this candidate has no instrument for the same structural reason its neighbours in `solutionsMissingInstruments` do not.

Unvalidated. Agent-ideated on 2026-08-29; a human to review.

## Definition of done — and it is not a command

"Replay the recorded expiries and check whether last-line age would have separated the slow runs from the stuck ones"

There is deliberately no instrument. The bar is: at least 8 of 10 replayed expiries classified correctly by last-line age alone. Settling it needs a person to read past each expiry in their own session history and label what the subject actually did next — ground truth that is not in this repository, against a helper that is not in it either.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Sequencing:** this is the most expensive of the three candidates, needing a change at every call site that starts a long job. Run the replay before building any of it — it is a paper exercise over sessions that already happened and it can kill the candidate for the price of ten minutes.

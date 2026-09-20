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

## 2026-09-20 — "where the mechanism would live" is not an open question: it is one line in this repository, and a spec already asserts on it

Short, and it corrects a paragraph of this node's body rather than adding evidence.

**The claim being corrected.** This node states: "**Where the mechanism would live is an open question.** The `await` helper is on the session's PATH, supplied by the harness, not in this repository. No spec in this product's `test/` can reach it, so this candidate has no instrument for the same structural reason its neighbours in `solutionsMissingInstruments` do not." Every clause of that is false, and the same false premise is recorded on the sibling candidate "A repeated wait on the same condition resumes and doubles its budget automatically, up to a ceiling set once by hand", where it is corrected at length this pass.

**What was read.** `src/loop/wait.ts` and `test/loop/wait-primitive-affordance.test.ts`, both whole and untruncated via `ost_read_repo` (`"truncated": false`).

**The helper is authored here, and the exact sentence this candidate wants to replace is a literal in it.** `renderWaitShim()` in `src/loop/wait.ts` emits the whole POSIX `sh` script, including the expiry line — `gave up after ${waited}s; the condition still exits $rc.` on stderr. That is, verbatim, the "the condition still exits 1" verdict this node's opening paragraph proposes to turn into a gradient. The mechanism would live where that string is composed. It is not an open question and it is not in the harness.

**And the spec already asserts on that line, so the fixture cost is zero.** The block `the shim is a working wait, not a string that measures well` writes `renderWaitShim()` to a temp dir at mode `0o755`, runs it through `execFileSync`, and the case `a condition that never holds gives up on the bound rather than hanging` asserts exactly `expect(r.stderr).toContain("gave up after")`. A spec that runs a condition which emits progress and then stalls, and asserts the expiry names the subject's last line and its age, fails today on an assertion against a shim that runs correctly and reports only `exits $rc` — the strong kind of red, not the `no-spec` kind.

**One thing the source changes about the candidate's cost, and it cuts in this node's favour.** The body says this is "the most expensive of the three candidates, needing a change at every call site that starts a long job." Half of that is already done: the shim captures the subject's output every attempt — `out=$(eval "$cond" 2>&1)` — and prints its tail on exit. What is missing is not capture but *time*: nothing timestamps an attempt, so last-line age cannot be computed. The per-call-site discipline the body worries about is still real for subjects that emit no progress at all, but the waiter already holds the text it would need to report, which no section here had established.

**What this does NOT change.** The Definition of done stays humans-required and is untouched: classifying ten replayed expiries as slow or stuck needs a person reading past each one in their own session history, and that ground truth genuinely is not in this repository. The instrument described above measures a different belief — feasibility, whether the expiry can carry the gradient at all — which is not on the tree, and creating it is an attended pass's call rather than this surface's. Nothing here argues the candidate should be built; the sequencing note stands, and the replay is still the cheap thing to run first.

**Limits.** Both files were read, not run, and nothing was executed. That the installed shim matches the renderer is inferred from the renderer being its only source, which the spec's `the shim needs nothing but sh` case supports but does not prove. Whether last-line age actually separates slow from stuck is exactly what the humans-required test asks and is untouched here. No rung moved, no instrument set, no status changed, no node created. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.

_Method: first-party `ost_read_repo` full reads of `src/loop/wait.ts` and `test/loop/wait-primitive-affordance.test.ts`. Observed structure of the product's own code and spec suite; it grounds feasibility, not desirability._

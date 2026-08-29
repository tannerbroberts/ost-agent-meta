---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Ask someone with the Monitor tool's implementation open whether a wait that blocks on job exit is accepted where the polling forms are refused]]

**Risk category: feasibility.**

Stated so it could be false: *the unattended surface will accept a wait that blocks on a job's exit — a PID wait, or the harness's own background-task handle — without refusing it the way it refuses the polling forms.*

**Why it is the riskiest belief under this candidate, rather than the obvious one.** The obvious risk is that adopted semantics are too thin (two-valued, no liveness). That is a known cost, written into the candidate's prose, and a cost that is known is not a risk. The real risk is that the door this candidate proposes walking back through is still shut. `await` exists *because* the platform's waiting forms were refused: "The Monitor tool refuses the exact commands an unattended run needs to check on its own background work" records a `command_substitution` rejection, a multi-part `until … done` loop refused with "the following parts require approval", and a `tail` blocked for reading outside the session's working directory. This workspace's own standing correction then names `await` as the prescribed replacement and explicitly forbids the shell-chaining alternative.

If those refusals still stand for job-control waits too, this candidate is not a cheaper trade-off — it is a proposal to adopt something that cannot run here, and it should be retired rather than sequenced against its siblings.

**Why answering this first is worth more than it costs.** A positive answer does more than clear this candidate: it would make both siblings unnecessary, because an accepted platform wait that blocks on exit removes the fixed cap and the completion-marker guess in one move. A negative answer retires this candidate outright for the price of one question. Either way it is the cheapest branch-shaping answer available here, which is why it should be settled before either sibling is costed.

**What it does not cover.** Nothing about whether an adopted wait is *good* — only whether it is permitted. A form that is accepted but two-valued still leaves the ambiguity the sibling candidate exists to remove.

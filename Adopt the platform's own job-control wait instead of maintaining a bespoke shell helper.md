---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The platform's own waiting forms are actually accepted on the unattended surface, where the bespoke helper was written to get around them]]

**Variation dimension: bought-vs-built. Position taken: adopted from outside, as-is; nothing built here.**

`await` is a helper this project put on the session's PATH. Retire it and wait the way the platform already waits: block on the job's exit rather than on a string appearing in its output. Backgrounding a command through the harness returns a handle to its output; a shell that started a child can block on its PID. Both are pre-existing, maintained by someone else, and correct about the one question the bespoke helper is worst at — whether the work is over — because they watch the job rather than a proxy for the job.

**The strongest thing in its favour is what disappears.** No cap to choose, no liveness check to write, no completion-marker convention for every caller to get right, and no second implementation to keep correct as the harness changes underneath it. The observed session's nine failures all trace to the helper's own two decisions — a fixed 300s, and a grep as the definition of done — and neither decision exists in an adopted primitive. This project already holds the general form of that argument on "Ship the helper with its own runtime rather than borrowing the machine's": helper scripts are where a dependency on the host's shell crept back in, and its own repo-grounded note records that the shell surface is down to exactly two files. This candidate is the same move applied to waiting specifically, and it argues for adopting rather than rewriting.

**What it gives up, plainly.** You inherit the adopted primitive's semantics and cannot extend them. Most job-control waits are two-valued — finished, or you stopped waiting — so the *still running* verdict the sibling candidate wants is not available and could not be added without building the thing this candidate declines to build. You also inherit its refusals: the Monitor surface on this very product already rejects command substitution and multi-part polling loops, which is recorded on "The Monitor tool refuses the exact commands an unattended run needs to check on its own background work". Adopting a primitive whose grammar is set elsewhere means the next grammar refusal is also inherited, and `await` exists in the first place *because* of those refusals. This candidate proposes going back through a door that was closed for a reason, and whoever picks it up should establish that the door has since opened.

**Against its siblings.** It is the cheapest to try and the only one that reduces the amount of code this project owns. It is also the only one whose success is not up to this project at all.

**What would make this the wrong pick.** If the reason `await` was written still holds — that the platform's own waiting forms are refused or unavailable on the unattended surface — then this candidate is not a trade-off, it is a proposal to use something that does not work here, and it should be retired rather than sequenced. That is a fact about the current Monitor grammar, it is cheap to establish, and it should be established before either sibling is costed, because a positive answer here makes both of them unnecessary.

Unvalidated, and ideated by an unattended pass. Not blind — see the note on the sibling candidate "Delete the wait: let harness-tracked work announce its own completion instead of being polled"; all three were composed in one context by one author.

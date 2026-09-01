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

## Definition of done — and it is not a command

"Ask someone with the Monitor tool's implementation open whether a wait that blocks on job exit is accepted where the polling forms are refused"

No command, on purpose: this one is humans-required. The bar is that at least 1 wait form blocking on job exit is confirmed accepted on the unattended surface. The deciding artefact is the Monitor tool's own permission grammar, which lives in the harness rather than in this repository, so no spec under `test/` can produce a verdict and composing candidate commands to see which are refused would only reproduce the discovery-by-violation this tree already records as a defect.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Sequencing against the siblings:** settle this before either sibling is costed. A `refuted` verdict retires this candidate for the price of one question. A `supported` verdict is stronger still — an accepted exit-blocking wait removes both the fixed cap and the completion-marker guess at once, which is most of what the other two candidates are for.

## 2026-09-01 — the door this node says must be established is observed ajar, and the cap it says disappears is observed intact

Kept short. One record, two findings, both qualified.

**Why this bears on this node specifically.** This node's body says the deciding question is cheap and should be settled before either sibling is costed: "If the reason `await` was written still holds — that the platform's own waiting forms are refused or unavailable on the unattended surface — then this candidate is not a trade-off, it is a proposal to use something that does not work here." Its Definition of done routes that to a person with the Monitor grammar open. This pass did not ask anyone; it read one evidence record in which both forms appear in the same session, which is a weaker instrument than the ask and is not a substitute for it.

**The record.** `TRANSCRIPT:861d61f8-0cc0-417f-8c53-094745c6395f`, captured at this firing's own ingest, mirrored 0d ago. Ten friction events from an unattended firing. Two lines matter:

- **tool_error** (Monitor): `Contains shell syntax (string) that cannot be statically analyzed`
- **retry** (TaskOutput) ×3, each carrying arguments: `{"task_id":"b1m9xmbii","block":true,"timeout":600000}`, `{"task_id":"binxzkhu1",...}`, `{"task_id":"bbecy42ci",...}`

**Finding one — the door is at least ajar, which is the direction that keeps this candidate alive.** In a single unattended session, Monitor's shell-polling form was refused on grammar while the platform's own exit-blocking form was invoked three times and produced no permission refusal and no grammar refusal. That is the contrast this node's parent assumption is worded around, observed rather than predicted. It is evidence toward `supported`, and it is exactly the sequencing this node asked for: a positive answer here is the one that makes both siblings largely unnecessary.

**Finding two — and it cuts against this node's headline claim.** This node argues that adopting removes the bespoke helper's two bad decisions, "a fixed 300s, and a grep as the definition of done", because "neither decision exists in an adopted primitive." The grep half survives that argument; the cap half does not. Every one of the three calls carries an explicit `timeout: 600000` — a fixed cap, chosen by the caller, in the adopted primitive. The cap did not vanish on adoption; it moved from 300s in the helper to 600s here. Whoever costs this candidate should strike the no-cap-to-choose item from the list of what disappears, and keep the rest.

**What the doubled signatures do and do not show.** Each of the three appears as a `retry`, which on this harvester means only that an identical `toolName + JSON.stringify(input)` signature occurred twice in the session. The detector consults no `tool_result` and no `is_error` — established first-party on the harvester candidate and recorded there — so this record cannot say whether the first call of each pair errored, expired, or returned fine and was simply re-read. Re-issue after a 600s expiry is *consistent* with the shape and is not established by it. Three distinct `task_id`s means these are three separate waits each issued twice, not one wait issued six times.

**Limits, stated so this is not over-read.** One record, one session, three calls. Absence of a refusal line is not proof of acceptance: this harvester files failures, so a call that was refused in some way the extractor does not classify would not appear here, and a successful *invocation* is not a successful *wait*. Nothing here touches whether the wait returned the verdict the caller needed. The humans-required Definition of done above is unchanged and still the thing that settles this node — a person with the Monitor grammar open can answer in one sentence what this record can only make likelier. No test was run, no result recorded, no rung moved, no instrument set, no status changed.

_Source: this firing's own `ost_ingest_inbox` output and the evidence body served by `ost_next_work({evidence})`. Observed behaviour of this product's own agent — it grounds usability, not desirability, and is not evidence that anyone wants anything._

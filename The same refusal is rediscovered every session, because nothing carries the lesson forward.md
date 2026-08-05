---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:5bbed804-1d15-44bd-8751-e1c0a87aed12'
created: '2026-08-02'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[I repeat one shell mistake five times in a session, because the first failure never said it was a class]]
[[A correction lives only as long as the session it was given in]]

Across at least six separate captured sessions the agent reached for the same shape — wait a while, then check on something — by writing `sleep 45` followed by a status command. Every time, the call was refused with the same message pointing at the right affordance. Every time, the agent adapted within the session. Every time, the next session started over and made the identical call.

The cost is small per instance and unbounded in aggregate: it is paid once per session, forever, and it never appears as a failure because the session recovers. What is missing is not a better error message — the message is already clear and already names the alternative. What is missing is any path by which a lesson learned at 14:00 on Tuesday is still known at 09:00 on Wednesday.

**The need:** I want what the agent worked out the hard way last session to still be known the next time it starts.

More than one way to address this: promote the recurring refusals into standing guidance the agent reads at startup, let a session write a durable note to itself that survives context, detect a repeat-offender pattern across sessions and surface it as a rule to adopt, or fix the affordance so the natural form is the working one.

## Provenance

Distilled from `TRANSCRIPT:5bbed804-1d15-44bd-8751-e1c0a87aed12`, a two-event session whose entire friction content is one shell-quoting error and one blocked sleep-then-poll.

Corroborated by the same blocked pattern in sessions `0d27cebf` (twice), `470cb94a` (twice), `4ff7b605`, `516fdfb8` and `5960b7ec` — seven or more instances of one refusal across seven days, none of which changed the next session's first instinct.

## Issues
- 2026-08-02 Possible gate conflict — flagged by the pass that created it, 2026-08-02. This node's parent "What the agent learns doesn't accumulate over time" is placed by the human-authorized prioritization of 2026-07-24 in the founder-theory lane, marked evidence-debt-gated: "no new siblings until a non-founder artifact cites the row." Whether this node clears that gate turns on a question the pass could not answer for itself — this node rests on `TRANSCRIPT:5bbed804` and twelve corroborating sessions, which is machine-captured rather than founder-authored, but it is still the product's own agent rather than an outside party. If "non-founder artifact" means anything not originating inside this building, the gate is not cleared and this node should wait. If it means evidence not composed by a person's assertion, it is cleared and this is the first row in that lane to have earned growth. A human's call, and the answer applies to every future node in the lane.
- 2026-08-05 Redundant section added by this pass, flagged by the pass that added it (2026-08-05). The `## Evidence` block appended at the foot of this node — three transcript ids showing the blocked sleep-then-poll refusal — restates what the node already says twice above it: the eleven-session census under "## Evidence — the blocked sleep-then-poll refusal, eleven sessions running" already lists all three ids, and the 2026-08-04 corroboration section lists two of them again. It was written as a probe, to find out whether citing an evidence id in a body clears it from `ost_next_work`; it does not, and that finding is recorded on "Evidence that fits no layer keeps coming back, so the pass never runs out of work" where it is useful. Left in place rather than rewritten because `ost_edit_node` on this node would mean re-authoring five overlapping census sections at once, and a botched consolidation loses prose that only git would hold. **The larger issue a human should settle:** this node now carries five sections making substantially the same census across four passes, and it is the clearest instance in the vault of the accumulation the rollup was introduced to stop. It wants one consolidated census with a running count, done deliberately by someone who can check nothing distinct is lost — not another append.

## Corroboration — the same three lessons, unlearned across eight days (unattended sweep, 2026-08-03)

Twenty-two sessions were read in full this pass. Three refusals recur in a way that is hard to read as anything but a lesson that does not persist — and one of them recurs *inside a single session*.

**1. `(eval):1: == not found` — nine times, three sessions.** Session `a615eb46` produced it **five times in a row**, as five separate tool calls. `b7aae32d` produced it three times, `97546e2f` once. The shell's answer never changed; neither did the agent's next attempt. Five identical refusals in one session is the strongest form of this evidence available: it is not memory failing between sessions, it is the lesson failing to carry forward across a handful of minutes.

**2. The glob that matches nothing — four sessions.** `no matches found: /Users/tanner/dev/ost*` (`5e5c119d`, then again in `8fc8d6e3`), `no matches found: src/vault/*.ts` (`e42cd03d`), `no matches found: test/tmp*` (`516fdfb8`). Same shell, same class, four separate discoveries.

**3. A workflow script written in TypeScript — twice.** `4ff7b605` and `516fdfb8` both submitted a workflow script and got `Invalid workflow script: Script parse error` back, and in both cases the refusal itself spelled out the answer: *"Workflow scripts must be plain JavaScript — common causes are TypeScript syntax (type annotations, interfaces, generics)"*. The tool taught the lesson the first time and had to teach it again.

The pattern across all three is the same: **the refusals are well-written and each one is discarded when the call that provoked it ends.** Nothing in the loop converts a refusal into a constraint the next composition is checked against — the diagnosis this node already makes, now with a repeat count attached.

_Source: `TRANSCRIPT:a615eb46-cc50-41a9-a77f-931c0dc67db0`, `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd`, `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68`, `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18`, `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1`, `TRANSCRIPT:e42cd03d-b2a4-44ba-989a-9e01cc368f77`, `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d`, `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` — observed behavior from the agent's own transcripts. Grounds usability, not demand._

## Evidence — the blocked sleep-then-poll refusal, eleven sessions running

Observed behaviour, captured mechanically from session transcripts. The identical refusal — a `sleep N` followed by a poll command, blocked with the advice to use `Monitor` with an until-loop or `run_in_background` — is hit fresh in eleven separate sessions across nine days. No session inherits the correction the previous one was given.

- `TRANSCRIPT:0d27cebf-9b5d-4cff-906c-0134512573bc` — blocked twice in one session (`sleep 25`, then `sleep 60`)
- `TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866` — `sleep 240`, then `sleep 45`
- `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` — `sleep 45`
- `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` — `sleep 45`
- `TRANSCRIPT:87a025f8-c6b0-474f-9a13-0b5ec5c922ea` — `sleep 30`
- `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` — `sleep 45`
- `TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538` — `sleep 45`
- `TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff` — `sleep 25`
- `TRANSCRIPT:a615eb46-cc50-41a9-a77f-931c0dc67db0` — `sleep 25`
- `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd` — `sleep 45`
- `TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129` — `sleep 45`

Ten of the eleven were the agent waiting on a CI check (`gh pr checks <n>`), which is the same want recorded under the sibling opportunity about waiting for a check it cannot subscribe to — but the need this evidence grounds is narrower and separate: the correction was delivered, in full, every single time, and was never once retained.

Evidence class: observed behaviour of the agent's own usage. It grounds usability, not desirability, and is not outside-user evidence of want.

## The cleanest instance yet: the same glob, two sessions, twenty-six hours apart

Two transcript captures contain a byte-identical failing command:

- `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1` (2026-07-24T21:55Z) — its *only* friction event: `Exit code 1 … (eval):1: no matches found: /Users/tanner/dev/ost*`
- `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18` (2026-07-25T00:02Z) — `Exit code 1 … (eval):1: no matches found: /Users/tanner/dev/ost*`

Same path, same unquoted glob, same zsh refusal, twenty-six hours apart, in two sessions with no memory of each other. This is the node's claim reduced to its smallest possible form: one lesson, learned twice, at full price both times.

It is a better instance than a within-session repeat because it removes the competing explanation. A mistake repeated inside one session can be attributed to inattention — the agent had the first failure in context and did not read it. Here the second session *could not* have read it. Nothing was forgotten; there was never anywhere for it to be remembered. That distinction matters for what would fix it: within-session repetition argues for a better error message, and cross-session repetition argues for a store, because no message can reach a reader who was not there.

**Where the same shape shows up again.** The blocked-`sleep` refusal is the higher-volume case of the identical pattern — nine sessions between 2026-07-24 and 2026-08-04 each independently issued a `sleep`-then-poll composition and each independently learned it was refused. That census is recorded on "My loop spends its time waiting for a check it cannot subscribe to" because the *want* there is a subscription; what makes it also this node's evidence is that the refusal text names the remedy every time, and nine sessions still arrived without it.

_Provenance: two friction records from the transcript adapter, machine-captured, no narrator. Observed behavior of this product's own agent; grounds usability, not desirability. Unvalidated — for human review._

## Corroboration — eight further sessions, one identical refusal (2026-08-04 sweep)

Eight sessions captured since this node was written each contain the same refusal, in the same shape: the run reaches for `sleep <n>` followed by a poll (usually `gh pr checks <n>`), and the harness blocks it with a message that names the remedy outright — "To wait for a condition, use Monitor with an until-loop".

- TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837 — 2026-07-29, `sleep 45`
- TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538 — 2026-07-29, `sleep 45`
- TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff — 2026-07-29, `sleep 25`
- TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866 — 2026-07-30, `sleep 240`
- TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d — 2026-07-30, `sleep 45`
- TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68 — 2026-07-30, `sleep 45`
- TRANSCRIPT:87a025f8-c6b0-474f-9a13-0b5ec5c922ea — 2026-07-31, `sleep 30`
- TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc — 2026-08-04, `sleep 25`

Five days, eight sessions, zero drift in the shape of the mistake.

What the volume adds is one sharpening worth carrying into any solution under this node: **the lesson is not missing, it is mis-placed.** The refusal text already contains the complete correction, delivered at the exact moment of the error, and the run complies with it that turn every time. It still does not survive into the next session. So a candidate that works by improving the error message is addressing something these eight records show is not the constraint — the message was already right. What fails is that the correction lives in a transcript nobody re-reads, rather than anywhere the next session looks before it composes a command.

_Recorded as corroboration during the 2026-08-04 unattended pass. These eight evidence items remain unmapped in `ost_next_work`, because counting an item as corroboration of an existing need has no representation in the sweep — see the pass note on "An acknowledgement that records a decision not to act, and takes the item off the sweep". Observed behavior, mechanically captured; grounds usability, not demand._

## History
- 2026-08-05 unlinked "Refusals are written back as a standing corrections file every session reads first" — re-parented under "A correction lives only as long as the session it was given in" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "The second identical failure is answered differently from the first" — re-parented under "A correction lives only as long as the session it was given in" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Refusals the tool can prevent become refusals the tool never issues" — re-parented under "A correction lives only as long as the session it was given in" — this solution answers that need, not the categories beside it

## Evidence

Three separate sessions each hit the *same* harness refusal, days apart, with no sign that any of them had learned it from the ones before:

- `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` — `Blocked: sleep 45 followed by: gh pr checks 17 head`
- `TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538` — `Blocked: sleep 45 followed by: gh pr checks 9 head -20`
- `TRANSCRIPT:87a025f8-c6b0-474f-9a13-0b5ec5c922ea` — `Blocked: sleep 30 followed by: gh pr checks 25 head -20`

The refusal message names the correct alternative every time, and every time it is spent on one session and then discarded. This is observed behaviour of the agent's own tool use — it grounds usability, not desirability, and is not evidence anyone outside wants this.

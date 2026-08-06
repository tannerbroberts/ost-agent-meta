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

Across many separate captured sessions the agent reached for the same shape — wait a while, then check on something — by writing `sleep 45` followed by a status command. Every time, the call was refused with the same message pointing at the right affordance. Every time, the agent adapted within the session. Every time, the next session started over and made the identical call.

The cost is small per instance and unbounded in aggregate: it is paid once per session, forever, and it never appears as a failure because the session recovers. What is missing is not a better error message — the message is already clear and already names the alternative. What is missing is any path by which a lesson learned at 14:00 on Tuesday is still known at 09:00 on Wednesday.

**The need:** I want what the agent worked out the hard way last session to still be known the next time it starts.

More than one way to address this: promote the recurring refusals into standing guidance the agent reads at startup, let a session write a durable note to itself that survives context, detect a repeat-offender pattern across sessions and surface it as a rule to adopt, or fix the affordance so the natural form is the working one.

## Provenance

Distilled from `TRANSCRIPT:5bbed804-1d15-44bd-8751-e1c0a87aed12`, a two-event session whose entire friction content is one shell-quoting error and one blocked sleep-then-poll. Corroborated by the running census below.

Evidence class throughout: observed behaviour of this product's own agent, captured mechanically from session transcripts with no narrator. It grounds usability, not desirability, and is not outside-user evidence that anyone wants this.

## Running census — four refusal classes, none of which carried forward

One census, maintained across passes, replacing six overlapping sections written on 2026-08-02, 2026-08-03, 2026-08-04 and 2026-08-05. Add new sightings to the tables below rather than appending another section. Window to date: **2026-07-24 → 2026-08-04.**

**1. Blocked sleep-then-poll — 13 sessions, 15+ occurrences.** The run writes `sleep <n>` followed by a poll (usually `gh pr checks <n>`), and the harness blocks it with a message naming the remedy outright: *"To wait for a condition, use Monitor with an until-loop"*.

| Session | Sighting |
| --- | --- |
| `TRANSCRIPT:0d27cebf-9b5d-4cff-906c-0134512573bc` | twice in one session — `sleep 25`, then `sleep 60` |
| `TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866` | twice — `sleep 240`, then `sleep 45` |
| `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` | `sleep 45` |
| `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` | `sleep 45` / PR 17 |
| `TRANSCRIPT:5bbed804-1d15-44bd-8751-e1c0a87aed12` | one blocked sleep-then-poll (this node's originating record) |
| `TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc` | `sleep 25` (2026-08-04) |
| `TRANSCRIPT:87a025f8-c6b0-474f-9a13-0b5ec5c922ea` | `sleep 30` / PR 25 |
| `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` | `sleep 45` / PR 18 |
| `TRANSCRIPT:995b8ab1-5e55-4a5c-b05d-aaed9e1d7538` | `sleep 45` / PR 9 |
| `TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff` | `sleep 25` / PR 10 |
| `TRANSCRIPT:a615eb46-cc50-41a9-a77f-931c0dc67db0` | `sleep 25` |
| `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd` | `sleep 45` |
| `TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129` | `sleep 45` |

**2. `== not found` — 4 sessions, 10 occurrences.** A bash-ism inside `[ ]` meeting a zsh that will not take it. `a615eb46` produced it **five times in a row as five separate tool calls**; `b7aae32d` three times; `97546e2f` once; `5e5c119d` once in its `====` form.

**3. A glob that matches nothing — 4 sessions.** zsh's nomatch error, where the identical command under bash would have passed the glob through and succeeded. `no matches found: /Users/tanner/dev/ost*` (`8fc8d6e3`, then again in `5e5c119d`), `no matches found: src/vault/*.ts` (`e42cd03d`), `no matches found: test/tmp*` (`516fdfb8`).

**4. A workflow script written in TypeScript — 2 sessions.** `4ff7b605` and `516fdfb8` both submitted one and got `Invalid workflow script: Script parse error` back. In both cases the refusal itself spelled out the answer — *"Workflow scripts must be plain JavaScript — common causes are TypeScript syntax (type annotations, interfaces, generics)"*. The tool taught the lesson the first time and had to teach it again.

## What the volume establishes

**The lesson is not missing, it is mis-placed.** This is the single most important thing the census says, and it rules out an entire family of candidate solutions. The refusal text already contains the complete correction, delivered at the exact moment of the error, and the run complies with it that turn every time. A candidate that works by improving the error message is addressing something these records show is not the constraint. What fails is that the correction lives in a transcript nobody re-reads, rather than anywhere the next session looks before it composes a command.

**The cross-session repeats are stronger evidence than the within-session ones, and the census holds both.** Two captures contain a byte-identical failing command twenty-six hours apart: `8fc8d6e3` (2026-07-24T21:55Z) and `5e5c119d` (2026-07-25T00:02Z), both `(eval):1: no matches found: /Users/tanner/dev/ost*`, in two sessions with no memory of each other. That form removes the competing explanation — a repeat *inside* one session can be blamed on inattention, since the agent had the first failure in context and did not read it, but the second session here *could not* have read it. Nothing was forgotten; there was never anywhere for it to be remembered. The distinction decides what would fix it: within-session repetition argues for a better message, cross-session repetition argues for a store, because no message reaches a reader who was not there.

**And the five-in-a-row run isolates the variable from the other side.** `a615eb46` producing `== not found` five consecutive times is the lesson failing to carry across a handful of *minutes*, not days — so whatever is absent is absent at every timescale, not only across restarts.

**A pre-committed bar for anything built here.** Thirteen sessions hitting one refusal, machine-recorded, is the baseline. A mechanism that carries lessons forward should reduce that count; one that does not reduce it has not worked.

## Relationship to neighbouring nodes

Ten of the thirteen sleep-then-poll sightings were the agent waiting on a CI check, which is the same raw event recorded under "My loop spends its time waiting for a check it cannot subscribe to". These are not duplicates and should not be merged: the want there is a subscription, and the want here is retention. What makes the same event evidence for this node is that the refusal named the remedy every time and thirteen sessions still arrived without it.

The three candidate solutions that used to hang directly here were re-parented on 2026-08-05 onto the child "A correction lives only as long as the session it was given in", which is where the solution space now lives. This node reads as underserved in `ost_next_work` for that reason — it is a parent opportunity now, not a gap.

## Issues
- 2026-08-02 Possible gate conflict — flagged by the pass that created it, 2026-08-02. This node's parent "What the agent learns doesn't accumulate over time" is placed by the human-authorized prioritization of 2026-07-24 in the founder-theory lane, marked evidence-debt-gated: "no new siblings until a non-founder artifact cites the row." Whether this node clears that gate turns on a question the pass could not answer for itself — this node rests on `TRANSCRIPT:5bbed804` and its corroborating sessions, which is machine-captured rather than founder-authored, but it is still the product's own agent rather than an outside party. If "non-founder artifact" means anything not originating inside this building, the gate is not cleared and this node should wait. If it means evidence not composed by a person's assertion, it is cleared and this is the first row in that lane to have earned growth. A human's call, and the answer applies to every future node in the lane.
- 2026-08-05 **Resolved by consolidation.** The prior entry here recorded that this node carried five (then six) sections making substantially the same census across four passes, called it the clearest instance in the vault of the accumulation the rollup was introduced to stop, and said it wanted one consolidated census done by someone who could check nothing distinct was lost — explicitly not another append. That consolidation is the body above. The blocker it named (`ost_edit_node` unavailable, and re-authoring five overlapping sections risking prose only git would hold) no longer applies: the tool exists on the unattended surface, and the full prior body was read before the rewrite. Every session id from all six sections is in the census table, and the four distinct analytic points are kept under "What the volume establishes". Recovery of the prior wording, if any of this is judged wrong, is `git show` on the commit before this edit.
- 2026-08-05 Standing note for future passes — a finding recorded on "Evidence that fits no layer keeps coming back, so the pass never runs out of work" applies here: citing an evidence id in a body does **not** clear that item from `ost_next_work`. Several of the transcript ids in the census above therefore remain listed as unmapped evidence forever, because counting an item as corroboration of an existing need has no representation in the sweep. That is a tooling gap, not a reason to create a duplicate opportunity for each one, and it is the reason this node accumulated six censuses in the first place.

## History
- 2026-08-05 body edited — Correcting the previous edit, which included the two child wikilinks at the top of the prose. `ost_edit_node` reattaches the tag-and-links header itself, so those lines appeared twice and would have failed the single-backlink invariant in `ost_check`. Prose is otherwise byte-identical to the consolidation committed moments earlier; only the two duplicated link lines are removed.

- 2026-08-05 unlinked "Refusals are written back as a standing corrections file every session reads first" — re-parented under "A correction lives only as long as the session it was given in" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "The second identical failure is answered differently from the first" — re-parented under "A correction lives only as long as the session it was given in" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Refusals the tool can prevent become refusals the tool never issues" — re-parented under "A correction lives only as long as the session it was given in" — this solution answers that need, not the categories beside it
- 2026-08-05 **the three entries above were restored by hand, not re-performed.** They were present before this pass and were dropped when `ost_edit_node` rewrote this node's body; they are reinstated verbatim from a read of the file taken before the edit. No edge changed as a result of the restoration — the re-parenting they describe happened on 2026-08-05 as written, and this line records only that the record of it was lost and put back. Ordering within this section is therefore not chronological; these three precede the `body edited` entries above them.
- 2026-08-06 unlinked "Waiting on a slow external check burns the session, because every obvious way to wait is refused" — Detached ahead of folding this node into "My loop spends its time waiting for a check it cannot subscribe to". Its own Issues section (2026-08-06) concluded that its only distinguishing content — the rediscovery cost — is what THIS parent already holds, leaving it carrying the intersection of two needs the tree keeps separately. Detaching first so the merge does not hand the survivor a second parent and break single-parent.

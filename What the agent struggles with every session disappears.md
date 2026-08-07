---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-transcript-ingestion.md'
created: '2026-07-24'
evidence: assertion
---
#Opportunity #unvalidated #needs-customer-interview #evidence/assertion
[[The friction that matters leaves no error behind]]
[[The same refusal is rediscovered every session, because nothing carries the lesson forward]]
[[The friction I hit leaves no record behind, so nothing can be learned from it]]

**The need (customer's voice):** "The agent gets confused, asks the same question again, stalls on the same step — and all of that is thrown away when the session ends. The clearest usage data this product has ever produced is being deleted every day."

**Why it matters:** A subset of the evidence-famine need, addressing a channel that already exists and is currently discarded. The agent running the OST is the product's most active user; every question, uncertainty, retry, and stall it hits is *observed behavior* (non-founder, non-stated) about where the product is hard to use. Unlike recruiting outside users, this channel needs no one's permission.

**Litmus test:** More than one way — harvest transcripts into the inbox, emit structured friction events at the point of stall, have the agent file its own confusions, mine commit/tool-error history. Passes.

**Caveat for a human:** Dogfood friction is usage data about *one* user who is not a paying customer, so it grounds usability far better than it grounds demand. It should not be allowed to substitute for the outside-user evidence the parent opportunity is about.

Evidence: `INBOX:2026-07-24-opp-transcript-ingestion.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Post-session transcript harvester" — re-parented under "The friction I hit leaves no record behind, so nothing can be learned from it" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "In-the-moment friction events filed by the agent" — re-parented under "The friction I hit leaves no record behind, so nothing can be learned from it" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Mine tool errors and retries from run logs" — re-parented under "The friction I hit leaves no record behind, so nothing can be learned from it" — this solution answers that need, not the categories beside it

## Issues
- 2026-07-25 Mis-parent flag (2026-07-24 review): the node's own caveat concedes dogfood friction must not substitute for the outside-user evidence its parent ('I can't tell if anyone outside my own head wants this') is about — a child that explicitly does not deliver the parent's need. Proposed reparent to an evidence-channel/instrumentation row; human to confirm.
- 2026-08-02 **Hygiene — the transcript channel emitted two evidence records for one piece of work (found 2026-08-02, flagged not repaired).** `TRANSCRIPT:16e9596b-7c8f-445b-a8ff-f822ed211ea5` (8 events) and `TRANSCRIPT:7e982096-36c5-4ac2-a23f-75865bc4bf8e` (7 events) carry the same seven `AskUserQuestion` events, in the same order, with the same text; their ingest timestamps are five seconds apart (`2026-07-28T20:39:26.291Z` and `2026-07-28T20:39:31.909Z`). That is one session, forked or resumed, harvested twice under two session ids. The instance is small; the shape is not. Every count taken over this channel — including the twenty-five-record census recorded on this node — silently double-counts a resumed session, and the ingest ledger cannot notice because the ids genuinely differ, so deduplication would have to be by content or by parent-session id, neither of which the channel records. Left in place rather than repaired, per the append-only rule; the census above states 25 records / 24 distinct sessions so the double-count is visible rather than absorbed. One occurrence, so it is filed as a product bug rather than raised as an opportunity — a second would make it a pattern. Belongs on the standing product-bug list on "OST-Agent (meta)" alongside the empty-annotation and wrapped-wikilink defects.
- 2026-08-07 Reported under-served (0 solutions), but this pass deliberately did not ideate under it, because the need as stated appears to have been largely met by shipped work and the node has not been re-read since. The transcript channel now harvests this vault's own sessions mechanically: the `ost_ingest_inbox` call opening the 2026-08-07 pass captured 3 new friction records, and the standing backlog stood at 76, each one an automatically extracted list of that session's tool errors, retries, permission denials and clarifying questions. Struggles are no longer disappearing — they are being recorded in volume without anyone carrying them in. What has replaced this need is narrower and is now tracked separately: recorded struggle has nowhere to land once the need it evidences is already in the tree (see "Evidence that only confirms a need I already recorded still arrives as work I have to clear"). Recommended for a human: re-word this node to whatever part of the original need the harvester does not cover, or mark it `deferred` as overtaken. Adding three solutions to it in its current form would be ideating against a problem the product has already solved.

## Evidence — eleven session traces and three usage rollups (mapped 2026-08-02)

Captured mechanically by the transcript and usage channels, covering 2026-07-25 to 2026-07-31. Recorded here rather than distilled into new opportunities: individually these are builder-toolchain slips, not unmet needs. What makes them evidence for *this* node is that they repeat across independent sessions and nothing carried the lesson from one to the next.

**Transcript channel — 11 sessions, 40 friction events.** `TRANSCRIPT:` ids `08ab58d6`, `424486ec`, `470cb94a`, `516fdfb8`, `87a025f8`, `97546e2f`, `a615eb46`, `b7aae32d`, `e335a680`, `f48dc76d`, `fd2c6d71`. Two patterns dominate and both are pure repetition:

- **zsh quoting — `(eval):1: == not found`, 9 occurrences across at least two sessions** (`a615eb46` ×5, `b7aae32d` ×3+). The same malformed comparison, retried unchanged, in sessions that never saw each other's failure.
- **`Blocked: sleep N followed by gh pr checks …`, 5 occurrences across 4 sessions** (`470cb94a`, `516fdfb8`, `a615eb46`, `b7aae32d`, `e335a680`). Each time the harness answered with the same correction — use an until-loop, or run in background — and each subsequent session made the identical call again.

The remainder are one-offs that carry no cross-session lesson: TypeScript errors mid-refactor (`e335a680`, `b7aae32d`), `Edit` old_string mismatches (`424486ec`, `516fdfb8`), a Workflow script written in TypeScript instead of JavaScript (`516fdfb8`), a 2-minute Bash timeout on a polling loop (`f48dc76d`), a `CronList` retry (`fd2c6d71`).

**Usage channel — 3 daily rollups, 217 calls.** `USAGE:2026-07-25` (108 calls, 0 failed, 3 sessions, p50 3ms), `USAGE:2026-07-26` (93 calls, **62 failed**), `USAGE:2026-07-27` (16 calls, 0 failed). The 2026-07-26 spike is the one number worth a human's eye: 75 of that day's 93 calls were `ost_annotate`, and the sampled failures are `no such node: probe` / `no such node: x` — a session probing the tool surface with throwaway node names, plus one `ost_create_node` refused for a literal `"undefined"` evidence class. That last one corroborates "A tool call I got slightly wrong destroyed the note I was filing" and the guard that now refuses it.

**What this does and does not support.** It is `observed`-rung on the agent's own behaviour and grounds usability only — per each record's own header, it is explicitly not outside-user demand data and must not be counted toward "I can't tell if anyone outside my own head wants this". The claim it does support is this node's: a repeated, mechanically-visible failure mode existed in nine sessions and no session started better-informed than the last.

## Evidence — the remaining twelve session traces (mapped 2026-08-02, second pass of the day)

The morning pass dispositioned eleven traces and three usage rollups above. This closes out the rest of the transcript channel: twelve more sessions, **38 friction events**, covering 2026-07-26 to 2026-08-02. `TRANSCRIPT:` ids `06eba571-9780-458a-b384-da5abe101e6f`, `16e9596b-7c8f-445b-a8ff-f822ed211ea5`, `4ff7b605-da1d-4f2e-8c05-ec6408118837`, `5960b7ec-960c-4700-9e0b-2b68c3519e92`, `5bbed804-1d15-44bd-8751-e1c0a87aed12`, `748498c4-31fb-4110-9012-464c441a463f`, `7e982096-36c5-4ac2-a23f-75865bc4bf8e`, `92cc492d-3bc1-4f30-abc3-4cae8f436c4e`, `995b8ab1-5e55-4a5c-b05d-aaed9e1d7538`, `a0eb3fd4-5a36-44c1-93fc-ac8b48258cff`, `a83f0269-c09e-45a3-a1f3-68f601b476c9`, `e42cd03d-b2a4-44ba-989a-9e01cc368f77`.

**Both cross-session repeats continued, in sessions that never saw each other's failure.**

- `(eval):1: == not found` — one more session here (`5bbed804`), on top of `a615eb46` (×5) and `b7aae32d` in the earlier batch. The same malformed shell comparison, retried unchanged.
- `Blocked: sleep N followed by gh pr checks …` — **five more sessions** (`4ff7b605`, `5960b7ec`, `5bbed804`, `995b8ab1`, `a0eb3fd4`), on top of four in the earlier batch. The harness printed the same correction every time — use an until-loop, or run it in the background — and the next session made the identical call again. **Nine sessions, one mistake, nine identical corrections, no accumulation.**

The remainder are one-offs carrying no cross-session lesson: a `git` divergent-branch hint (`06eba571`), `sed` against a moved path and a perl typo (`748498c4`), a zsh glob and an unknown skill id and a `cp` overwrite prompt (`e42cd03d`), a `Workflow` script written in TypeScript (`4ff7b605`), `Edit` old_string mismatches (`4ff7b605`, `5960b7ec`, `995b8ab1`), a failing vitest run (`995b8ab1`), a `cd` into a directory that does not exist (`a0eb3fd4`), and two bare shell-quoting slips (`92cc492d`, `a83f0269`).

Across both batches that is **twenty-three sessions and 78 mechanically-captured events**. This node's claim — that nothing carries the lesson from one session to the next — is now measured over an order of magnitude more sessions than when it was written, and the measurement did not soften it.

**Fifteen of the thirty-eight events are not tool failures at all.** `16e9596b` (×8) and `7e982096` (×7) consist entirely of `AskUserQuestion`: the pass halting to ask a human. The harvester records those as friction because they interrupt a session, but what they observe is a different need, and the corroboration is filed on "I need the tree's output to be actionable by compute alone, because my hours don't exist" rather than counted here.

**Rung.** `observed` on this vault's own behaviour, per each record's `TRANSCRIPT:` provenance and its own header. Explicitly not demand evidence, and it must not be counted toward "I can't tell if anyone outside my own head wants this".

## Census addendum — `TRANSCRIPT:0d27cebf`, captured mid-pass 2026-08-02

One new session record arrived during the fourth unattended pass of the day: 10 events (tool_error ×9, clarifying_question ×1). It changes no claim on this node and is recorded because the count it extends is the claim.

**The cross-session repeat continues.** `sleep N` followed by another command was blocked twice in this single session — `sleep 25 && tail …` and `sleep 60 && gh pr checks …` — with the harness returning the same correction both times, pointing at `Monitor` with an until-loop. This morning's census put that pattern at **nine sessions, corrected identically nine times, learned zero times**. This is the tenth session and the eleventh and twelfth corrections. Nothing carried the lesson from the first nine into this one, which is precisely what this node says happens.

**The rest is harness noise, not product friction, and is recorded as such:** four path errors against directories that do not exist on this machine (`/Users/tanner/dev/ost-benchmarks/bin/`, `/Users/tanner/dev/ost-agent-meta`, two missing log files), one `Edit` string-not-found, one two-minute timeout, one non-zero exit from a status roll-up. **No `ost_*` tool appears among the failures**, which extends the finding already recorded on "The friction that matters leaves no error behind" to a twenty-fifth session: the channel built to watch this product work keeps capturing the coding harness the agent runs inside.

**Disposition: acknowledged, no new node.** No customer need is revealed that this tree does not already hold, so distilling an opportunity from it would be inventing one. Like the other 41, it will keep reporting unmapped until "Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity" exists.

## Refinement on one census entry — unattended sweep, 2026-08-02 (sixth pass)

The 11-session census above files `424486ec` under the one-offs, as an `Edit` old_string mismatch alongside `516fdfb8`. Re-reading that session's three events together suggests they are one mechanism rather than two unrelated misses, and the correction is worth having on the record even though it changes no node.

The session's two `Edit` failures are bracketed by a `clarifying_question` whose text reads: *"Another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago…)"*. That is a coherent single story — a concurrent writer moved the files under a read the agent had already taken, and both edits then failed against a picture that had gone stale. Read that way it is not a typo class at all; it is a stale-read class, and the second `Edit` error even carries the harness's own hint that the mismatch is "likely elsewhere in old_string," which is what a whole-file change looks like from inside a targeted edit.

**Deliberately not raised as an opportunity.** One occurrence, which is the bar this node's own census applies to `16e9596b`'s double-harvest; a second instance would make it a pattern about concurrent writers rather than an anecdote about one session. It is also adjacent to "Two agents sharing my vault can trample each other", which makes the same claim scoped to the vault rather than to the source repo — whether that node should widen or a sibling should exist is a human's call, not this pass's.

_Provenance: `TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab`, re-read in full this pass. Correction to a prior pass's classification, appended rather than edited._

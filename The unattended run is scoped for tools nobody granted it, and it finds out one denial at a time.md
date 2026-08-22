---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Preflight the run's tool demands against its grant and stop at turn one]]
[[The run's report leads with what it was refused, so a denied night cannot read as a quiet one]]
[[Derive the permission allowlist from the skill's own allowed-tools, so the two lists cannot drift]]

I set a run going while I am asleep, and it spends the night being told no.

Five unattended firings recorded the same thing. Session `8a9777ad` asked for `ost_flag_humans_required` four times in a row and was denied four times, then asked for `ost_check` and was denied. Session `6e66c934` asked for the same tool four times and was denied four times. Sessions `21d0f730`, `7449e571` and `1a8f25fb` each hit it too — `ost_check` in all three, plus `ost_debt` and `ost_status`. Across those five sessions the message is identical every time: "Claude requested permissions to use X, but you haven't granted it yet." Reading the product's own source hit the same wall: `Glob` was refused on `/Users/tanner/dev/OST-Agent` in four separate runs, and `ost_read_repo` failed differently but for the same reason — "no product repos configured".

The instructions the run is given name these tools. The grant it is handed does not include them. Nothing compares the two before the run starts, so the mismatch surfaces as a denial in the middle of work, after the run has already decided what it was going to do and against a person who is not there to say yes.

Two things are wrong with this and only one of them is the missing permission. The other is that a denial to an unattended run is indistinguishable, from where I sit the next morning, from work that simply was not needed. The run reports what it did; it does not report the shape of what it was stopped from doing. So a night of denials reads as a quiet night.

What I want is to know before I walk away that the run can do the job I set it, and to be told plainly if it could not.

## Provenance

Cited record: `TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd`. The same pattern is independently recorded in `6e66c934-24d8-4200-b6f2-7af23002c478`, `21d0f730-05c0-4cf8-8cd2-ecdea5444bba`, `7449e571-40b5-47b6-a1cd-3b2c1c85322e`, and `1a8f25fb-1259-4b80-8b53-32fbfde38e54`. All five are marked in the transcript as "this vault's own unattended firings — nobody was watching". Frontmatter carries one id because citations are matched exactly; the others are named here in plain text.

This is the agent's own usage captured mechanically. It grounds usability, not desirability.

## Observed again during the pass that created this node

This node was distilled from five transcript records, and then the same thing happened to the pass writing it. Two denials, first-party rather than reconstructed:

- `ost_debt` — "Claude requested permissions to use mcp__ost-agent__ost_debt, but you haven't granted it yet." Called to find which assumption tests sat beneath which solutions, which is the one question that bucket of work needs answered.
- `ost_flag_humans_required` — same message. Called to label three tests whose own prose names outside people as the measurement.

That makes six independent sessions, and this one is the strongest evidence of the set: the other five are recollections assembled by an adapter from transcripts, while this one was observed as it happened by the agent that then had to work around it.

Both denials had a workaround and neither was free. The `ost_debt` question was answered instead by reading `ost_read_tree`, overflowing its output cap, and grepping the vault's files directly — four calls and a spilled tool result to replace one. The `ost_flag_humans_required` calls could not be worked around at all: three tests that should carry a `lane:` marker still do not, and the finding was written into their `## Issues` sections as prose, where nothing that reads the field will see it. A reader checking lanes mechanically still sees three unlabelled tests that look runnable.

That second case is the sharper form of this opportunity than the one the body above describes. A denied read costs turns. A denied *write* leaves the tree carrying a claim in a place no gate reads, and the pass that recorded it looks, from its own summary, like it handled the item.

Provenance: this pass, 2026-08-06. Not an ingested record — no adapter has captured this session yet, and citing an id for a session that has not ended is the exact fault flagged on four nodes elsewhere in this vault this morning.

## Final tally for the pass of 2026-08-06

Three distinct tools denied, not two. `ost_check` was called last, to verify the tree's invariants after roughly forty writes, and refused with the same message as the others.

That third one is the worst of the three and worth separating from the rest. `ost_debt` cost turns and had a workaround. `ost_flag_humans_required` left three labels unwritten and was recorded as prose. `ost_check` means **the pass could not verify its own output.** Forty-odd writes went in — new opportunities, solutions, assumptions, tests, instruments, appended definitions of done — and the one deterministic check that would say whether any of them broke an invariant was unavailable to the run that made them.

The tree happens to be clean: the four `unresolved-citation` issues cleared during the pass, and the final `ost_next_work` returned `hygieneIssues: []`, which is computed over every node. So there is a second channel and it gave a good answer. But that is luck about which surfaces overlap, not a property anyone designed, and `ost_next_work` reports hygiene rather than the full invariant set — a wrapped wikilink or a second backlink is `ost_check`'s to catch and this pass has no assurance about either.

Which sharpens what this opportunity is really about. The cost of a denied grant is not the turn. It is that an unattended run's ability to check itself is a permission, and when that permission is missing the run does the work anyway and reports it with a confidence it has not earned. Every summary this pass wrote about its own correctness rests on a gate it was not allowed to open.

Grants this pass needed and did not have: `ost_check`, `ost_debt`, `ost_flag_humans_required`, and read access to the product repository (both by path and via `product.repos`, which is unconfigured).

## The denied set is stable, which changes what kind of problem this is — 2026-08-06, later pass

A second unattended pass the same day hit **exactly** the set the tally above names: `ost_debt`, `ost_flag_humans_required`, and `Glob` on the product directory. Nothing new was denied and nothing previously denied was granted. (`ost_check` was not reached this time; the other three matched.)

Deliberately not appending another census — the repetition itself is the only new fact, and this node has been asked once already to stop accumulating restatements.

What the repetition establishes is worth one line, because it rules out a reading. A grant gap that varied between runs would be a flaky or context-dependent permission, and the fix would be defensive retry or graceful degradation. A grant gap that reproduces identically across independent firings is a **fixed, known, enumerable list that nobody has applied to the allowlist.** There is nothing to discover. The four tools were named in the tally above at 2026-08-06, and the next pass needed the same four.

That is direct corroboration of the premise under "Derive the permission allowlist from the skill's own allowed-tools, so the two lists cannot drift" — the two lists have not drifted unpredictably, they are statically different in a way that has now been measured twice and would be measured the same way every future pass. It also means the cost is not a one-off: every pass pays the same workaround tax, and every pass records the same finding, which is itself a small instance of the lesson-never-carries-forward problem this vault tracks separately.

One consequence specific to this firing: three more tests that name outside people as the measurement could not be labelled, for the same reason as last time. "Hand-compute unblock counts and see if the operator's pick changes", "Five-minute orientation task on a static mock" and "Test do operators get value with remote push off" all sit under solutions listed in `solutionsMissingInstruments`, and all three are correctly answered by a person rather than a command. The disposition they need is `humansRequired`, the tool for it is denied, and so they will be offered again next pass as solutions missing instruments — where the only available action is to write a command that cannot honestly measure them.

### Correction to the section above — all four, not three

That section said `ost_check` "was not reached this time" and claimed a three-of-four match. It was reached, at the end of the pass, and it was denied with the identical message. The match is **exact: all four.** `ost_check`, `ost_debt`, `ost_flag_humans_required`, and reads of the product repository — the same four the 2026-08-06 tally named, denied in the same way to an independent firing.

The correction strengthens rather than weakens the point, and it reproduces the specific harm that tally called the worst of the three. This pass made roughly thirty writes — a new opportunity, six solutions, six assumptions, six tests, several appended definitions of done, one annotation — and could not run the one deterministic check that would say whether any of them broke an invariant. Every claim it makes about its own correctness rests, again, on a gate it was not allowed to open. `ost_next_work` returned `hygieneIssues: []` afterwards, which is the same second channel and the same piece of luck: it reports hygiene, not the full invariant set, so a wrapped wikilink or a second backlink introduced by this pass would not appear there.

Two passes, same four tools, same unverifiable ending.

## The gap is not drift, and applying the list would have been the wrong fix — 2026-08-06, from the product repo

Both passes above end at the same inference: a fixed, enumerable list "that nobody has applied to the allowlist." That reads as an instruction to apply it. Reading the product repo — which neither pass could do, which is why neither could check this — says applying it would have overwritten a decision.

`src/knowledge/ruleset.ts:332-335` withholds exactly these tools from `/ost-pass` on purpose, and says so in terms: a skill grant "does not move a single cell of that table" and must not "drift into the unattended sweep by association." The reasons are per-tool and recorded (`test/release/examples-allowlist.test.ts`, `CONTAINED_ON_PURPOSE`): `ost_flag_humans_required` is R7's containment, `ost_check` was judged exposition rather than a step, `ost_rank_source` keeps source-finding and source-promoting out of one agent's hands. The measured facts in this node are all correct. The conclusion drawn from them is not: **the skill declares 22 tools, the surface grants 16, and the difference is a decision rather than an oversight.**

So the defect is one layer over from where this node puts it. It is not that the grant is too narrow. It is that the pass is handed the *declaration* (SKILL.md, as its system prompt) and never told which part of it does not apply here — and under `-p` a tool outside the grant is denied with no message, so there is no way to learn it except by spending a call. That is the mechanism behind every symptom recorded above, including the one this node calls the worst: a pass reports its writes as "unverified" as though an instrument failed, when `ost_check` was never offered to it.

Shipped as OST-Agent PR #69: `autonomous-pass.sh` derives the withheld set from the two lists it already holds and names it in the system prompt, stating that writes are unverified *by design*. It renders nothing when the lists agree, so retiring a containment removes the section instead of leaving a stale copy. The grant is untouched.

**One thing this does not fix, and it is the fourth item in the tally.** Product-repo reads failed for a different reason — `product.repos` is unconfigured in this vault's `ost.config.yaml`, so it is a missing configuration rather than a withheld grant. `ost_read_repo` *is* granted on this surface. The three solutions filed under "The agent's repo sight fails mid-pass" are the right place for it and remain open.

**A second finding, from the same reading, that no pass could have seen.** Both loops printed `Permission deny rule "SlashCommand" matches no known tool` on every firing for four days. That was not a stale-name nit: Claude Code renamed `SlashCommand` to `Skill`, an inert deny rule provides no coverage, and the delegation capability the deny list exists to refuse was reachable from an unattended pass the whole time. Fixed in the same PR. The general shape is worth more than the instance — **a guard that names something which no longer exists reads exactly like a guard that works**, and the only signal was a warning line that looked like noise.

## Census of the whole transcript corpus — 113 denials across 34 sessions (unattended sweep, 2026-08-06)

This node has been argued from individual sessions. This is the count across every transcript record the vault holds, taken by grepping the evidence corpus for the harness's denial string rather than by reading sessions one at a time.

**113 occurrences of `haven't granted it yet`, spread across 34 distinct sessions.** That is the volume: a denial is not an occasional mis-scoping, it is roughly three and a third wasted calls in every session that hits one, and it recurs in 34 separate runs that had no memory of each other.

**The distribution is the interesting part — it is heavily concentrated.** The worst sessions burned 9, 8, 7, 6, 6, 6 and 5 calls on tools that were never going to answer (`03a79a59` 9, `28d14def` 8, `6e66c934` 7, `49d6b2d3` 6, `8a9777ad` 6, `21d0f730` 5, `3b9eaea5` 5, `491c205c` 5). A run does not learn from the first denial and stop — it works through the surface one refusal at a time, which is exactly what this node's title claims and what the count now shows at scale.

**Same tools, over and over.** In the two most recent sessions the denied calls are `ost_flag_humans_required` (four times in one session), `ost_status`, `ost_check` and `ost_debt` — the four tools the unattended surface withholds by design. `3b9eaea5` (2026-08-06) also shows two denied `Glob` reads of the product directory before the agent gave up on it. So the denials are not random exploration; they are a stable set of tools the pass keeps being scoped for and keeps not having.

**Why this is stronger than the sightings it supplements.** A per-session record leaves open that the mis-scoping was one bad configuration. 34 sessions with the same shape rules that out. And the corpus contains the natural experiment: sessions running under a prompt that *names* the withheld tools still produced denials for exactly those tools, which says a written warning at the top of the context does not prevent the calls. That narrows the solution space here the same way the census on "The same refusal is rediscovered every session" narrows its own — the remedy is not better wording, it is either a preflight that fails before work is planned or a grant that matches the scope.

**A pre-committed bar for anything built here.** 113 denials across 34 sessions, machine-recorded, is the baseline. A preflight that names the missing tools at turn one should drive the per-session count to at most one; anything that leaves a run discovering denials mid-pass has not worked.

_Method: a grep of every `TRANSCRIPT_*.md` record in this vault's evidence folder for the harness's denial string, counted per file. Observed behaviour of this product's own agent, captured mechanically with no narrator — it grounds usability and feasibility, not demand. The 34 session records remain listed as unmapped evidence in the sweep; citing them here does not clear them, per the standing finding on "Evidence that fits no layer keeps coming back, so the pass never runs out of work". Corroboration only — no test was run, no result recorded, and the node's rung is unchanged._

## Evidence — TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de

Source: TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de (observed, the agent's own unattended firing; usability, not demand).

Ten friction events, six of them denials, and the shape is the point: `ost_flag_humans_required` was requested and denied **four times in the same session**. The run did not learn from the first refusal, because a denial arrives as a per-call error and nothing on the surface carries it forward to the next call. `ost_status` and `ost_check` were each discovered denied the same way, one call apiece.

This is the same need this node already states, now with a count attached: the cost of discovering scope one call at a time is not one wasted call per missing tool, it is one wasted call per *attempt*.

## The fix shipped, and this is the first pass measured against the bar — 2026-08-07

Not another sighting. The census above fixed a bar in advance — "113 denials across 34 sessions, machine-recorded, is the baseline. A preflight that names the missing tools at turn one should drive the per-session count to at most one; anything that leaves a run discovering denials mid-pass has not worked." This pass ran under the mechanism that bar was written for, and the count is **zero**.

**The mechanism is confirmed live, not inferred.** This pass's system prompt carries a section headed "What this surface withholds", naming `ost_check`, `ost_debt`, `ost_flag_humans_required`, `ost_gate`, `ost_rank_source` and `ost_status`, pointing at `test/release/examples-allowlist.test.ts` (`CONTAINED_ON_PURPOSE`) and `src/knowledge/ruleset.ts` for the per-tool argument, and instructing the pass to "report your writes as unverified-by-design rather than as a tool that failed." That last phrase is verbatim what this node recorded PR #69 as shipping. It is the same artifact, in the wild, one day later.

**The count.** No call was made to any of the six withheld tools, so no denial was returned. Baseline for comparison: 113 denials across 34 sessions, 3.3 per session, worst sessions 9, 8, 7, 6, 6, 6 and 5. Bar: at most one per session. Zero clears it.

**Read the caveats before treating this as a result, because it is not one.** No result has been recorded — `ost-agent result` is a human's. Four things weaken the reading, and they compound. n=1. The observer is the subject, so this is an agent reporting its own compliance. The pass had read the bar it was being measured against before it acted, which is the sharpest form of that problem. And a pass that makes no denied call is not distinguishable, from the outside, from a pass that had no occasion to make one. The third is the one worth weighing hardest: a preflight that works only when the run knows it is being counted has not been shown to work.

**What it does narrow, and it is a claim this node made.** The census argued that "sessions running under a prompt that *names* the withheld tools still produced denials for exactly those tools, which says a written warning at the top of the context does not prevent the calls." As stated that is now too strong. Those sessions were handed the skill's *declaration* of 22 tools and left to discover the subtraction; this one was handed the subtraction itself — which six do not apply, the reason each was withheld, and the fact that calling one is denied silently and buys nothing. Naming the tools did not prevent the calls; naming what was taken away, with reasons, coincided with none being made. One firing cannot say which half of that difference did the work, and the census's underlying point — that better wording is not the remedy — survives either way.

**The other half of the tally is unrepaired, and the split is the useful signal.** PR #69's own note said it did not fix the fourth item, product-repo reads. Confirmed today, first-party: `Glob` on `/Users/tanner/dev/OST-Agent` was denied again, and `product.repos` is still absent from this vault's config. So of the four grants this node has tracked since 2026-08-06, three were closed by a prompt section derived from a decision the product already held, and the fourth — one line of config — is now five passes old. A human comparing effort to effect has that contrast to work from. The repo-sight half is already recorded four times over on "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed" and is deliberately not restated there again by this pass.

_First-party observation by the unattended sweep of 2026-08-07, of its own opening context and its own call log. Observed behaviour of this product's own agent: it grounds feasibility and usability, not demand. No test was run, no result recorded, and this node's rung is unchanged._

## Second consecutive pass at zero, which is what the n=1 caveat asked for — 2026-08-09

The section above measured the shipped preflight at zero denials and then listed four reasons not to believe it, the sharpest being n=1. This is n=2. Recording it in three lines rather than another census, because the only new fact is that the count repeated.

**The count.** Zero calls to any of the six withheld tools, so zero denials. The "What this surface withholds" section was present in this pass's opening context, naming `ost_check`, `ost_debt`, `ost_flag_humans_required`, `ost_gate`, `ost_rank_source` and `ost_status`, with the same instruction to report writes as unverified-by-design. Baseline remains 113 denials across 34 sessions, 3.3 per session; bar remains at most one per session.

**Three of the four caveats still stand, and one of them has now hardened.** The observer is still the subject; the pass had still read the bar before acting; and a pass that makes no denied call still cannot be distinguished from one that had no occasion to. That last is *weaker* here than it was last pass, in a way worth one sentence: this pass had a live occasion. It reached the `solutionsMissingInstruments` bucket, found five entries that needed `humansRequired` rather than a command, and `ost_flag_humans_required` is precisely the tool for that — the tool four separate sessions in the census burned calls on. It was not called, because the withheld list said not to. That is the mechanism working against a real demand rather than in its absence, which is the specific thing n=1 could not show.

**What is still not shown.** Whether it works when the run does not know it is being counted. Two firings, both of which read the bar, cannot separate "the preflight works" from "the preflight works on a run that has been told about the preflight." Nothing available to an unattended pass can separate those, and this node should stop trying — the separation needs a firing that was never handed the section, which is a human's experiment to arrange.

**The repo-sight half is unrepaired for the sixth time** and is recorded on its own node, not restated here.

_First-party observation by the unattended sweep of 2026-08-09, of its own opening context and its own call log. Agent self-observation: grounds feasibility and usability, not demand. No result recorded; the node's rung is unchanged._

## Third consecutive pass at zero, and the corpus splits into two populations — 2026-08-10

**The count, first, because that is the cheap part.** Zero calls to any of the six withheld tools, so zero denials. n=3. The "What this surface withholds" section was present in this pass's opening context, naming the same six with the same instruction to report writes as unverified-by-design. Baseline and bar unchanged.

This pass had a live occasion, as the pass before it did, and a sharper one. It found five solutions in `solutionsMissingInstruments` carrying `status: shipped` and several more whose tests can only be answered by a person — `ost_flag_humans_required` is the tool for the second class and is the single most-denied tool in the whole corpus. It was not called. That is the third firing running against a real demand for a withheld tool and not making the call.

**What is actually new: the 113 was two different problems added together.** Every census on this node has counted the harness's denial string as one population. Re-counted this pass by the *shape* of the denial, over the whole evidence corpus:

| Class | Occurrences | Sessions | Per session |
|---|---|---|---|
| `permissions to use mcp__…ost_*` — a withheld tool | 83 | 28 | 3.0 |
| `permissions to read from <path>` — a directory | 42 | 36 | 1.2 |

127 total across 47 sessions, up from the 2026-08-06 baseline of 113 across 34, counted with the identical string so the two are comparable.

**The split inverts this node's prioritisation, and that is the finding.** Every argument here has been made from concentration — the worst sessions burning 9, 8, 7 calls, all of them withheld-tool denials. That framing made the tool class look like the whole problem and the product-repo grant look like a footnote. By reach it is the other way round: the path-read class appears in **36 sessions to the tool class's 28**. It is the more widespread of the two and always has been; it was invisible because it costs about one call per session instead of three, so it never showed up in a tally sorted by volume. A run hits a directory denial once, concludes the path is not available, and stops — which is the *absence* of this node's title behaviour, and is why it never produced the signature that got attention.

So the fourth grant, the one that is a single line of `product.repos` config and is now six passes old, was never the small half. It reaches more firings than the three that were closed by PR #69, and it has been triaged behind them on a count that could not see it.

**A bar for the unrepaired half, stated separately from the tool bar.** 42 denials across 36 sessions, 1.2 per session, is the baseline for product-directory reads. Configuring `product.repos` should drive it to zero; anything that leaves a firing discovering the path unavailable mid-pass has not worked. The existing bar — at most one withheld-tool denial per session — is untouched and is still met.

**Caveats, and two are new.** The three standing ones hold: the observer is the subject, the pass had read the bar before acting, and three firings that all knew about the preflight cannot separate it working from it working on a run that was told. New: this firing's own `Glob` denial on `/Users/tanner/dev/OST-Agent` is **not** in the 42, because a session's transcript is filed after it ends — so the path-read count is one short of current and the direction of the error is known. And the two classes sum to 125 rather than 127; the residue is other denial shapes not broken out, so both rows are floors.

_Method: four counted `Grep` passes over every record in this vault's evidence folder, separating the denial string by the phrase that follows it. Agent self-observation of this product's own firings, captured mechanically — it grounds feasibility and usability, not demand. No test was run, no result recorded, and this node's rung is unchanged._

## Fourth-plus consecutive count at zero tool denials, and the unrepaired half keeps growing — unattended sweep, 2026-08-16

Recounted today by the same method as the prior censuses: `grep` of every `TRANSCRIPT_*.md` record in this vault's evidence folder, split by denial shape.

**Tool-denial class (`permissions to use mcp__…`): 83 occurrences across 28 sessions — unchanged from the 2026-08-10 count, to the occurrence.** No session recorded since has hit any of the six withheld tools. The streak this node has been tracking since the 2026-08-07 fix now covers a full week of firings, not two isolated passes.

**Path-read class (`permissions to read from <path>`): 59 occurrences across 50 sessions, up from 42/36 on 2026-08-10.** Fourteen more sessions hit a denied read of the product directory in the six days since, and it is now unambiguously the larger and still-growing half of this node's title, exactly as the 2026-08-10 section predicted it would remain once nobody was scoring by volume.

**One correction to the record.** `ost.config.yaml` now sets `product.repos: [/Users/tanner/dev/OST-Agent]` — its own comment dates the change to 2026-08-09, before the 2026-08-10 section that still called the grant unset. So `ost_read_repo`'s configuration gap is closed; the continuing denials are raw `Glob`/`Read` calls against the product directory made by whatever surface a firing is running on, which is a harness sandbox permission this vault's config cannot reach. That is a narrower, harder claim than "one line of config, unapplied" — it is a permission this product does not control, growing at roughly the same rate the tool-denial class has stopped growing at.

_Method: `rg -c "haven't granted it yet"` / `"permissions to use mcp__"` / `"permissions to read from"` over `.ost-agent/evidence/TRANSCRIPT_*.md`, read directly rather than through the transcript adapter. Agent self-observation of this product's own firings; grounds feasibility and usability, not demand. No test run, no result recorded, node's rung unchanged._

## The streak broke, and the break went unrecorded for four days — recount, unattended sweep 2026-08-21

The section above (2026-08-16) states: "Tool-denial class (`permissions to use mcp__…`): 83 occurrences across 28 sessions — unchanged from the 2026-08-10 count, to the occurrence. No session recorded since has hit any of the six withheld tools." **That is no longer true, and it stopped being true the day after it was written.**

Recounted this pass by the same method — a grep of every `TRANSCRIPT_*.md` in this vault's evidence folder, split by denial shape:

| Class | 2026-08-10 | 2026-08-16 | **2026-08-21** |
|---|---|---|---|
| `permissions to use mcp__…` — a withheld tool | 83 / 28 | 83 / 28 | **91 / 29** |
| `permissions to read from <path>` — a directory | 42 / 36 | 59 / 50 | **82 / 69** |

**The whole of the tool-class increase is one session.** `TRANSCRIPT:90d8aeae-192e-4adf-9dd5-746832e3753e`, timestamped `2026-08-17T07:16:14.531Z`, is an unattended firing whose entire friction content is **eight consecutive denied calls to `ost_flag_humans_required`** and two retries. Not a mixed session with one slip in it — eight identical calls to the single most-denied tool in the corpus, made one after another, with nothing else attempted in between. 83 + 8 = 91, 28 + 1 = 29; the arithmetic closes exactly, so this session is the entire regression and there is no second one hiding in the count.

**Measured against the bar this node fixed in advance.** The 2026-08-06 census pre-committed: "A preflight that names the missing tools at turn one should drive the per-session count to at most one; anything that leaves a run discovering denials mid-pass has not worked." Eight is eight times that bar. Under the bar as written, this firing is a **failure**, and it is the first one recorded since the mechanism shipped. The three consecutive zeroes (2026-08-07, -09, -10) and the 2026-08-16 recount are not retracted — they happened — but "the streak covers a full week of firings" was already false when it was written and has been false ever since.

**What this pass cannot say, and will not guess.** Whether that firing's opening context carried the "What this surface withholds" section at all. Every zero-denial report on this node establishes the section was present *in the pass writing the report* — a pass can read its own prompt and no other. Nothing in the vault records what prompt any other firing was handed. So the two live readings are: the section was absent from that firing (a delivery failure in `autonomous-pass.sh`, which would make the mechanism sound and its wiring broken), or it was present and disregarded eight times (which would refute the mechanism outright). **These have opposite remedies and the evidence here cannot separate them.** A human with the loop's invocation log for 2026-08-17T07:16Z can settle it in one look; nobody else can.

**The finding that outlives whichever answer wins.** The bar existed, the measurement was mechanical, the failing record was captured within the hour — and the claim on this node still read "streak holds" for four days, because a census here is prose a pass writes by hand when it happens to recount. Nothing re-took the measurement; a pass had to choose to. That is a distinct need from the one this node names and it now has its own node, "A measured bar is only re-taken when a pass feels like it, so a fix reads as working long after it stopped", filed under the sweep-reporting category.

**The path-read class, meanwhile, is accelerating.** 42 → 59 → 82 occurrences and 36 → 50 → **69 sessions**, an increase of 23 occurrences across 19 further sessions in the five days since 2026-08-16. It is now recorded in more than twice as many sessions as the tool class and remains, per the 2026-08-16 correction, a harness sandbox permission this product's config cannot reach. Its own bar — "42 across 36 sessions is the baseline; configuring `product.repos` should drive it to zero" — is not merely unmet but moving the wrong way, and the 2026-08-16 correction explains why: `product.repos` was the wrong lever, because these are raw `Glob`/`Read` calls the vault's config never governed. That bar should be re-written by whoever owns it; this pass does not re-write a bar it did not set.

**Corroborated first-party, this pass.** `Glob` on `/Users/tanner/dev/OST-Agent` was denied to this firing too, with the same message, and `ost_read_repo` answered normally against the same directory — the separable-grants finding recorded on the sibling node, observed again. This firing's own denial is not in the 82; the count is a floor by one, and the direction of the error is known.

_Method: two `Grep` count passes over `.ost-agent/evidence/TRANSCRIPT_*.md`, plus a direct read of the 90d8aeae record and its frontmatter timestamp. Agent self-observation of this product's own firings, captured mechanically with no narrator — it grounds feasibility and usability, not demand. No test was run, no result recorded, and this node's rung is unchanged. The 29 and 69 session records remain listed as unmapped evidence; citing them here does not clear them._

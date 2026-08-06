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

---
type: Opportunity
source: 'agent-run:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Count a source citation in a node's prose as a mapping, wherever in the body it appears]]
[[Give a node a structured list of the sources it rests on, and a tool call to add one]]
[[Let a pass explicitly dispose of an evidence record it has read, naming what it corroborated]]

**The need.** The skill's own rule for evidence is "reuse, don't duplicate": when a new record corroborates a need already on the tree, append the corroboration to that node rather than minting a second opportunity saying the same thing. Passes here have followed that rule scrupulously for weeks. The queue does not register any of it. Every correctly-handled record stays in `unmappedEvidence` forever, and the count is now **363** — by a wide margin the largest number in the sweep, and the single biggest reason a pass cannot reach `done`.

## The natural experiment, taken from one sweep's own output

This is not inferred. Today's `ost_next_work` returns `unmappedEvidence` alphabetically from the start of the set, so absence from the head of that list is conclusive rather than an artifact of the 25-item cap. Three records sitting within four characters of each other in that ordering behave differently:

| Evidence id | How the tree records it | In `unmappedEvidence` today? |
|---|---|---|
| `TRANSCRIPT:0b98ae8c-…` | not cited anywhere | **yes** |
| `TRANSCRIPT:0d27cebf-…` | carried as the `source:` of "I probe for files that were never there, because nothing hands me the layout of the workspace I am in" | **no — drained** |
| `TRANSCRIPT:0e0cd6f3-…` | cited in the prose of "The agent has to guess what resources it's actually working with", under a dated Corroboration heading with a full `_Source:_` line | **yes** |

`0d27cebf` sorts between the other two and is simply not in the list; the other two are. The only difference between `0d27cebf` and `0e0cd6f3` is **which part of the file names them** — one is a frontmatter `source:`, the other is prose. `TRANSCRIPT:09ec7cd2-…`, cited by name in two separate nodes' corroboration sections, is also still listed.

So the predicate for "mapped" reads the `source:` field and nothing else. And a node has exactly one `source`. Between those two facts, an evidence record can only ever drain the queue by **causing a brand-new node to be created for it** — which is precisely the act the method tells a pass not to perform when the need already exists.

## Why this is a need and not a preference

The rule and the counter point in opposite directions, and a pass has to disobey one of them:

- Follow the method, corroborate the existing node, and the queue reports the work as never done. Repeat for weeks and you get 363 items that no amount of correct work will ever clear.
- Satisfy the counter, mint a new opportunity per record, and you get 363 near-duplicate nodes — the exact debt `near-duplicate` hygiene, `ost_merge_nodes` and the extent-overlap rules exist to prevent.

The incentive as built rewards the second. That nobody has taken it is a fact about the passes, not about the mechanism.

## Why it belongs under this parent

The parent names the general defect — the queue does not drain when the work is done — and already records four mechanisms of it: shipped solutions still asked for instruments, deferred opportunities still counted under-served, category buckets counted as needing direct solutions, and humans-required tests still listed as owing a command. This is the fifth, it is the same shape (a fact the product holds is applied to some analyses and not others), and it is larger than the other four combined.

**How it differs from its siblings, so it is not one of them wearing a new title:** every sibling concerns a **node** whose settled state the queue ignores. This concerns an **evidence record**, which is a different kind of object, drains through a different predicate, and would be fixed by different code. A repair to any sibling leaves all 363 in place.

## Litmus test — more than one way to address it?

Yes, and the candidates disagree about what a mapping *is*: count a prose citation as one; let a node declare several sources through a structured field; let a pass explicitly dispose of a record it has read and judged; or age records out on time and accept that some real needs go unmapped. Different mechanisms, different failure modes, genuine trade-offs. Passes.

## Limits of this finding, stated so it is not over-read

- **The predicate was not read in source.** It lives in `src/mcp/next-work.ts`, which is 74KB and would truncate on a single read; this pass probed its size and did not read it. The behaviour above is established from the tool's own output, which is strong evidence of *what happens* and no evidence of *how it is implemented*. A builder should confirm the predicate before changing it.
- **363 is the count of records, not of unmet needs.** Most of these are transcript friction records whose shapes this tree already carries; a mechanism that drained them would be recording that they were handled, not surfacing new work. Nobody should read a drained queue as more discovery having happened.
- **Whether an operator wants this queue to drain is unasked.** One could argue every record should stay visible until a human has seen it, and that a growing count is the honest signal. That is the design question and this node does not settle it.

⚠️ Unvalidated. Distilled by an unattended pass from its own tool output; no human has confirmed that a draining evidence queue is what they want. First-party observation of this product's own tooling — it grounds feasibility and usability, not demand. No command executed, no result recorded; rung at the `assertion` floor.

## 2026-10-13 — the count this node opens on is now 1017, nearly triple

A short note with a measurement. No new argument.

**The figure.** This firing's `ost_next_work` reports **1017** unmapped evidence items. This node opened at 363 on 2026-08-22. The stop condition the unattended loop pasted above this firing lists the same 1017 as the largest of its three `go` reasons.

**What was sampled, and what it showed.** Five records were read in full: `TRANSCRIPT:3541b3ed-…` (captured this firing), `030e5db3-…`, `00032886-…`, `0095203e-…` and `08e10880-…`. All five repeat shapes the tree already holds:
- withheld-tool and repo-read denials, under "A scheduled run finds out its tools are missing only after it has started";
- a brace in a Grep glob read as an alternation group, under "A string I meant literally is read as syntax, so the command fails instead of searching";
- Write/Edit refused because the file had not been read, under "The file changed after I read it, and the failed edit is how I find out";
- a Monitor command refused for containing command substitution, under the Monitor-grammar solutions.

None of the five held a need the tree does not already carry. `030e5db3` is still listed as unmapped even though "A scheduled run finds out its tools are missing only after it has started" has cited it under a `_Source:_` line since 2026-10-02. That is the predicate this node describes, seen again.

**What this firing did about it: nothing to the queue, on purpose.** It created no node per record. It also appended no fresh corroboration to the sibling nodes, which already carry several recurrence lines each, so one more would add length and no information. The three candidates under this node are where the count gets fixed, and choosing one is the operator's call.

**Limits.** 5 of 1017 records were read. They were the head of an alphabetical listing, not a random sample, so this is no rate over the whole set. All five come from this vault's own unattended sessions: they show how the agent uses the product, not what anyone wants. No `ost_check` on this surface, so this write is unverified by design.

## 2026-10-16 — the tail of the queue looks like its head

The 2026-10-13 section stated a limit: its five records "were the head of an alphabetical listing, not a random sample". This firing read six from the **other end** of the ordering. It got their ids from the evidence filenames and read each body through `ost_next_work({evidence})`: `ffb9eb47-…`, `fffde2fc-…`, `ffcee3f3-…`, `fe8409a0-…`, `fd10c391-…`, `f0f8fb56-…`. They are dated 2026-08-22 to 2026-10-15. It also read the one record this firing's ingest captured, `adedd3cc-…`.

**Result: 7 of 7 repeat shapes the tree already holds, and none holds a new need.** Here is what they contained:
- the prescribed `ost_ingest_inbox` / `ost_next_work` re-call, scored as `retry`;
- repo-path permission denials on Glob and Grep;
- a `read_repo` probe of a path that does not exist;
- `create_node` refusing a bar-less threshold and a malformed instrument;
- `append_to_node` refusing the reserved `## History` heading.

`adedd3cc` is 11 `retry` events. They are re-reads of the same head-of-queue evidence ids and the same held-opportunity body that this firing also read, so each firing re-derives the previous one's verdicts.

**What this does to the 10-13 limit.** The queue now has a sample from both ends that agrees. So it is more likely that the 1074 are mostly records of needs the tree already holds, and less likely that this is an artefact of always reading the head. It is still 12 of 1074, chosen by position rather than at random, so it does not give a rate.

_Method: seven `ost_next_work({evidence})` reads plus one filename Glob. This is observed behaviour of this agent's own surface. It grounds usability, not desirability. No node was created, no rung moved, and nothing was executed. `ost_check` is withheld here, so this write is unverified by design._

## 2026-10-17 — the middle of the queue looks like both ends

The 2026-10-16 section sampled the head and tail and noted the sample was still "chosen by position rather than at random". This firing read four records from the **middle** of the ordering, `5e5c119d-…`, `6e66c934-…`, `7c6f8edf-…` and `8a9777ad-…` (dated 2026-07-25 to 2026-08-06), plus `02912d97-…`, the one record this firing's ingest captured.

**Result: 5 of 5 repeat shapes the tree already holds, and none holds a new need.** Edit refused on an unread file; permission denials on withheld tools (`ost_flag_humans_required` four times in one session, `ost_check`, WebFetch) and on the product-repo path; a brace in a Grep glob; zsh `no matches found`; a rung-ceiling refusal on `create_node`; an unexpected `limit` parameter on Glob; and the prescribed `ingest`/`next_work` re-call filed as `retry`. `02912d97` is three `retry` events, each re-reading an evidence id (`030e5db3`, `08e10880`, `9e4847e5`) that earlier firings had already read and reported on this node.

**What this adds.** The queue has now been sampled at the head, the tail and the middle, 17 records in all, and every one repeats a need the tree already holds. That is still not a random sample and gives no rate. But "it is an artefact of where passes read" is now a weak explanation. The 1088 look like records of needs already on the tree, which the predicate this node describes cannot count as mapped.

_Method: five `ost_next_work({evidence})` reads and one filename Glob. This is observed behaviour of this agent's own surface. It grounds usability, not desirability. No node was created, no rung moved, and nothing was executed. `ost_check` is withheld here, so this write is unverified by design._

## 2026-10-18 — 12 of the 25 records at the head of the queue are already cited in node prose

Earlier sections showed the predicate one record at a time. This section counts a whole page. This firing's `ost_next_work` listed 25 `unmappedEvidence` ids (1107 total), and one Grep over the vault's node files (`*.md`) looked for each id. **12 of the 25 are cited by name in at least one node's prose and are still listed as unmapped.** For example, `0095203e-…` is cited in seven nodes, and `08e10880-…`, `00c3120a-…` and `024ceca3-…` are each cited on "The session tries to write a file before it has read it this run, and the guard fails the turn instead of reading first". The other 13 are cited nowhere.

**A second thing the same Grep showed.** The head-of-queue ids also turn up *inside later friction records*, for example `08e10880-…` in about a dozen other `TRANSCRIPT_*.md` evidence files. Each firing reads the head of the queue with `ost_next_work({evidence})`, and the harvester files those reads as `retry` events that name the ids. So reading the head creates new records that cite it. This firing re-read four records (`030e5db3`, `08e10880`, `00032886`, `0095203e`) that the 2026-10-13 section had already read and reported, before it noticed the overlap.

**Limits.** This is a literal substring match on an 8+4-character id prefix, one page of the queue, read at one moment. "Cited" means named in the prose, not judged correctly mapped. _Observed behaviour of this agent's own surface. It grounds usability, not desirability. No node created, nothing executed. Unverified by design (`ost_check` withheld)._

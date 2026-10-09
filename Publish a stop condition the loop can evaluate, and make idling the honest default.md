---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Whether an item is actionable is decidable mechanically, not case by case]]

The tree gains an explicit, computable answer to "is there anything worth doing right now?" — not a count of open items, but a predicate over them: work that is both outstanding and actionable by whoever is asking. A loop that evaluates it and gets false stops, reports that it stopped because there was nothing it could do, and costs nothing until something changes.

The distinction that makes this work is between outstanding and actionable. The current sweep reports plenty of outstanding items that no unattended pass may touch — tests only a human may run, evidence that cannot be mapped without inventing a need. Counting those as work is what creates the pressure to invent.

**Compared to the alternatives.** This is the cheapest of the three and the only one that requires no new infrastructure — the predicate is a function over state the sweep already computes. It is also the weakest, because it tells the loop when to stop and nothing about when to start again; pairing it with a wake signal is the obvious next move but is a separate solution.

**What would make this the wrong pick.** If "actionable" turns out not to be mechanically decidable — if it needs a judgement call per item — then the predicate becomes a place to hide the same ambiguity, and a loop reading it will be exactly as confused as before with more confidence.

## Definition of done

"Have two people independently label a full sweep's items as actionable or not, and compare"

```
npx vitest run test/loop/stop-condition.test.ts
```

Green means: the rule exists as data rather than prose, an empty sweep makes it evaluate true and the pass idles without writing, and a pass that writes while the condition holds fails. That last assertion is what makes idling the *honest* default rather than the polite one. Green does **not** mean the condition agrees with people; the two-labeller comparison stays with humans.

## History
- 2026-08-05 unlinked "Have two people independently label a full sweep's items as actionable or not, and compare" — moved under "Whether an item is actionable is decidable mechanically, not case by case" — the belief this test measures now has a node of its own

## 2026-10-05 — built, and on this vault it can never hold: all three of its live terms are ones the tree already records as unreachable from the surface it governs

This candidate's own "what would make this the wrong pick" is that "actionable" might not be mechanically decidable. The build answered a narrower question than that, and the gap is now measurable.

**What was read.** `src/loop/stop-condition.ts` (first 28KB of 28,677 bytes, through `ost_read_repo`). Its own docstring states the design: "Today they are exactly the five lists `ost_next_work` already computes `done` from, and the parity test pins that. The condition is therefore not a new predicate over the tree." Its rule for declaring a field not-actionable is stated on `solutionsAwaitingObservation`: "work no granted tool can reach is not work this loop may fire itself to do."

**This firing's verdict was `go` on three terms, and each one fails that same rule on this vault**, by findings already on the tree rather than by anything argued here:

- `unmappedEvidence` (889): drains only when a record becomes some node's frontmatter `source:`, so the only way to clear a record that restates a known need is to mint a duplicate node. That is "I map evidence the way the method says — onto an existing node — and the queue counts it as untouched". This pass read six of the records (four transcript, two usage) and all six restate needs the tree already holds.
- `underservedOpportunities` (1): the only entry is "The agent can decompose my goal but cannot acquire and test its own guesses about how to reach it", which carries a recorded human hold against unattended ideation. That node's 2026-09-09 section names the remedy as `ost-agent dispose`, which is a human's.
- `solutionsMissingInstruments` (72): a full-page census on "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue" found 25 of 25 shown entries non-instrumentable. That node's 2026-09-07 section found `src/eval/buildable.ts` consults no lane, and the one call that would relabel them (`ost_flag_humans_required`) is withheld from this surface.

**So the condition cannot change state.** It holds only when all five terms are zero, and on this vault three of them are pinned above zero by causes no unattended firing can touch. The usage records for 2026-10-03 and 2026-10-04 are consistent with that: 23 sessions and 306 calls, then 23 sessions and 318 calls, with 1 and 7 writes, every write an append or an annotate. The idle-breach check (`idleBreach`) still does its half, keeping firings from inventing structure. The half this candidate promised, a loop that "stops, reports that it stopped because there was nothing it could do, and costs nothing until something changes", is not reached on this vault.

**Where the defect actually lives.** It is not in this module, which evaluates faithfully. It is that "actionable" was taken to mean "a `done` term" rather than "a term some tool on the governing surface can decrement." A builder has two separable repairs. The first is per-term: fix each of the three upstream predicates, which each have their own node. The second is structural: make the parity test assert, per term, that at least one tool on `/ost-pass`'s grant list can reduce its count. Under that assertion a withheld relabel tool would show up in the classification itself instead of in sixty-eight sessions of usage trace. Which repair to pick is a design call and not this pass's.

**Limits.** The file truncated near `observeStopCondition`, so the code that wires it into `loop start` / `loop stop` was not read. The three unreachability claims rest on the cited nodes' own first-party reads, not on fresh reads of `next-work.ts` (74KB) or `buildable.ts` this pass. Usage-trace call counts are whole-vault and mix attended with unattended sessions. Nothing was executed, no rung moved, no instrument set, no status changed, no node created. The two-labeller test beneath this candidate is untouched and is still the only thing that can say whether the terms agree with people.

_Method: one `ost_read_repo` file read, one directory listing and one size probe, plus six evidence bodies read through `ost_next_work`. A first-party read of the product's source; it grounds feasibility, not desirability._

## 2026-10-08 — the `unmappedEvidence` term is refilled by the loop's own prompt, so fixing the three terms one by one would not reach `stop`

The 2026-10-05 section says three terms are pinned above zero and names per-term repairs. One of those terms is not just pinned. It is refilled on every firing, and the source is the loop's own instruction.

**Measured over `.ost-agent/evidence/`:** **132** transcript records contain one friction event and nothing else: `retry (mcp__ost-agent__ost_ingest_inbox): {}`. That is the second ingest that the unattended prompt's step 5 asks for ("Re-call `ost_ingest_inbox`… re-ingesting each iteration"). **510** records include at least one such line. This firing's own ingest captured another (`TRANSCRIPT:627046fa-a683-44ad-913a-5c6a1ce6a944`). A record that holds only a call the prompt required names no need, so no honest mapping can clear it.

**What changes for a builder.** Suppose a human cleared all 948 records today, with `dispose` or a many-to-one mapping. The next firing that follows its prompt would still put a new record in the queue, and the condition would read `go` again. So the per-term repair for `unmappedEvidence` is not enough unless the harvester stops counting calls the loop prescribed. That is the subject of the sibling candidate "A human-edited manifest of loop-prescribed call sequences the harvester suppresses", and it is now a prerequisite for this candidate, not an alternative to it. The other option is to drop the second ingest from the prompt. That is the operator's call, and so is the choice between the two.

**Limits.** These are counts from a grep over record bodies, not a classification by the harvester's own code. The count of 132 matches only the exact single-event form, so it is a floor. Nothing was executed, and no rung, status or instrument changed. `ost_check` is withheld on this surface, so this write is unverified by design.

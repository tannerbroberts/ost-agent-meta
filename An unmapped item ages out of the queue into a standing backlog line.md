---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Ageing an item out does not bury a novel one]]

**The idea.** An evidence item that has been offered to N passes and mapped by none stops being listed individually. It joins a single line — "62 items aged out, oldest 2026-07-24" — that is always visible and never expands unless asked for.

**Why this shape.** It is the only candidate here that makes no claim whatsoever about what the items mean. Nothing is discarded, nothing is asserted to be a duplicate, nothing is filed against a node. The queue simply stops presenting as fresh work something that eleven consecutive passes have declined to act on, which is information the sweep already has and currently ignores.

Worth stating plainly: this is the floor, not the answer. It is here because the two siblings both require judgement the surface may not be trusted with, and a tree needs a candidate that survives the decision that judgement is too expensive.

**How it compares to its siblings.**
- "An evidence item can be filed as corroboration of a node that already exists" is the ambitious one — it puts frequency on the tree. This one puts frequency nowhere; it just stops repeating the question.
- "The queue groups identical friction shapes into one item with a count" compresses by similarity and can be wrong about similarity. This compresses by age and cannot be wrong, because age is not a judgement.

**Where it fails, stated so it can be judged.** Ageing is a proxy for *irrelevant* and it is a bad one here. The items in this backlog were not skipped because they were uninteresting; they were skipped because the surface had no way to discharge them, which is a tooling gap. Ageing them out converts a visible tooling gap into an invisible one, and the count that made the gap arguable — "it has only ever grown" — stops being confrontational the moment it is one line.

The failure mode is therefore that this ships, the complaint goes quiet, and neither sibling ever gets built.

**Cost.** Lowest of the three. A counter per item and a summary line.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"A novel item survives the age-out that buries its neighbours"

```
npx vitest run test/evidence/age-out-preserves-novel.test.ts
```

Written without repo sight, so its first red is an absent file. Note that passing requires consulting something besides age — which, if it holds, means this candidate is less judgement-free than its body claims.

## 2026-08-29 — this is built, and the vault has simply not turned it on

**Read with repo sight, which the pass that wrote this node did not have.** `test/evidence/age-out-preserves-novel.test.ts` exists in the product's suite and holds two named tests. The first seeds twenty-one equally-old records — twenty repeating an already-mapped signature, one novel — and asserts that the twenty collapse into `agedOutEvidence: { count: 20, oldest: OLD }` while the novel one stays individually listed and every file stays on disk. The second asserts that **with no `evidence.ageOutDays` configured, nothing ages out no matter how old**.

**So the knob is `evidence.ageOutDays`, and this vault has not set it.** That is why `ost_next_work` returned `agedOutEvidence: { count: 0, oldest: null }` on 2026-08-29 while listing 457 unmapped items, 432 of them not even shown. The second test above is a precise description of the state this vault is in.

**Three corrections to this node's own text, stated rather than edited in.**
1. The `## Definition of done` block says the instrument was "written without repo sight, so its first red is an absent file." The file is no longer absent. Whether `npx vitest run test/evidence/age-out-preserves-novel.test.ts` is red or green today is not something this pass can know — it does not run tests — and it needs `ost-agent verify` to settle. But the weak `no-spec` red that block warns about is no longer the reason it would fail.
2. The body's central claim — that ageing "makes no claim whatsoever about what the items mean" and "cannot be wrong, because age is not a judgement" — is contradicted by the spec that was built for it. The implemented rule is **age AND redundancy with an already-mapped signature**, and the spec's own header says so: "AGE ALONE MAY NEVER COLLAPSE AN ITEM." The body already anticipated this in its closing line; the spec has now settled it. This candidate is not judgement-free, and the reader should not compare it to its siblings as though it were.
3. The body's stated failure mode — "this ships, the complaint goes quiet, and neither sibling ever gets built" — is worth re-reading against what actually happened. It did not ship *and* go quiet; it shipped and was never enabled, so the complaint has been loud (457 items) for a different reason than the one predicted.

**What a human could do in one line, and what it would and would not buy.** Setting `evidence.ageOutDays` in `ost.config.yaml` would collapse the redundant tail of the friction queue — the near-identical `tool_error`/`retry` session records that ten consecutive sweeps have declined to map — while, per the first spec test, leaving anything novel individually listed. What it would *not* do is discharge the underlying gap: those records were never skipped because they were uninteresting, they were skipped because an Opportunity carries one `source` id and the surface has no verb for "this record corroborates a node that already exists." That gap belongs to the sibling "An evidence item can be filed as corroboration of a node that already exists," and enabling age-out would make it less visible, exactly as this node's own **Where it fails** paragraph predicts.

**Not acted on by this pass.** `ost.config.yaml` is the operator's file and no tool on this surface writes it. Recorded here rather than on the Outcome because it is a fact about this candidate, not a ledger of the sweep.

## 2026-08-31 — the live age-out path is verified, and there are two different ageing mechanisms under similar names

Kept short. This closes an errand another node left open and corrects a reading trap that has already caught one pass.

**The errand being closed.** The 2026-08-31 section on "A human-edited manifest of loop-prescribed call sequences the harvester suppresses" states a limit on its own conclusion: "this pass read `src/ost/ageing.ts` and found it to be a different, replay-only module that by its own docstring 'changes what a live sweep reports' in no way, so the live age-out path was not verified here and someone should confirm it before turning the knob." This pass confirmed it first-party.

**The live path is the one the spec drives.** `test/evidence/age-out-preserves-novel.test.ts` imports `computeNextWork` from `src/mcp/next-work.js` and calls it as `computeNextWork(vault, dir, 3, NOW, undefined, AGE_OUT_DAYS)` — the sixth positional argument is the knob. That is the same function that serves `ost_next_work`, so the spec exercises the production sweep entry point rather than a parallel implementation. The 2026-08-29 section above therefore rests on the right artifact, and its conclusions stand unqualified: age-AND-redundancy is the live rule, and the second test pins that an unset `evidence.ageOutDays` ages nothing out no matter how old.

**The trap, stated because it is cheap to fall into.** `src/ost/ageing.ts` is a separate 13KB module exporting `replayAgeingRule` and `formatAgeingReplay` over an array of past `SweepObservation`s. Its docstring says outright that "nothing here changes what a live sweep reports." Crucially it implements a **different rule** from the live one: N consecutive passes on which an item was present and *untouched*, where a changed `signature` — the caller's answer to "what would look different if somebody had worked on this?" — resets the streak. The live rule keys on capture age plus redundancy with an already-cited signature. Same vocabulary, different predicates, different inputs. Anyone reading `ageing.ts` to learn what `evidence.ageOutDays` does is reading the wrong file, which is exactly what happened.

**The consequence that matters for the decision, and it cuts against an obvious move.** `replayAgeingRule` looks like the natural way to preview the knob before enabling it — it replays a rule over past sweeps and its formatter even states a judgement bar, "at most 2 in 10 aged-out items are judged to have mattered." It is not a preview. Because the two rules have different predicates, a replay showing that few items would have been buried says nothing about what `evidence.ageOutDays` would bury, and vice versa. A human who runs the replay to derisk turning on the knob would be reassured by a measurement of something else. If a preview of the live rule is wanted, it has to be built against the live predicate; none exists today.

**Limits.** Read-only. `src/mcp/next-work.ts` is 91,654 bytes and would truncate, so the age-out predicate's implementation was not read line by line — the claim that the spec drives the live path rests on the spec's own imports and call signature, which this pass read in full, plus `src/ost/ageing.ts` read in full. Nothing was executed, no result recorded, no instrument set, no rung moved, and `ost.config.yaml` is untouched — the knob remains the operator's call.

## 2026-08-31 (second firing) — the knob would reach at most a fifth of this vault's queue, because ageing reads a stamp four in five records do not carry

Kept short, and deliberately not a restatement of the two sections above: they establish *what* the live rule is, this establishes *what it would touch here*.

**The rule's input, read first-party.** `test/evidence/age-out-preserves-novel.test.ts` names it in a comment on its own fixture constant: "Ageing reads `fetchedAt` — when this vault pulled the record — rather than the item's own `timestamp`, which is the producer's field and would let a drop-folder note bury itself by dating itself 2019." The fixture accordingly hands `writeEvidence` an explicit `CAPTURED` argument for all twenty-one records. So the predicate's input is the capture stamp, not the record's own date.

**This vault's queue mostly has no such stamp.** This firing's own `ost_next_work` reported 494 unmapped records and said of them: "392 carry no capture stamp at all, so their age is unknown." Every row it listed carried `mirror.freshness: "undated"` with `fetchedAt: null`, except three stamped ones. That is 102 of 494 records — a fifth — with the field the rule reads.

**Consequence for the decision this node has been asking a human to make.** The 2026-08-29 section says setting `evidence.ageOutDays` "would collapse the redundant tail of the friction queue." On this vault, on today's records, it would collapse at most the redundant tail *of the stamped fifth*. The 392 undated records are the tail — they are the oldest, captured before stamping existed — and they are precisely the ones the knob cannot reach. A human who turns it on expecting the 494 to drop to a manageable list should expect a number no smaller than 392, and should not read that as the rule failing.

**The gap this exposes in the instrument, stated as a limit rather than fixed.** The spec above has two tests and both seed every record with a capture stamp. There is no case for a record whose `fetchedAt` is null, so the rule's behaviour on an undated record — never ages out, or ages out as infinitely old — is not pinned by the thing that would serve as a builder's definition of done. Four in five of this vault's live records take that untested branch. This pass did not set an instrument for it and should not: this node already carries a command, and replacing it would un-clear whatever observation that command has earned. The right repair is a third test case in the existing spec file, which is a builder's edit, not a tree write.

**Limits.** Read-only, nothing executed. `src/mcp/next-work.ts` is 91,654 bytes and truncates on this surface, so the predicate's own handling of a null `fetchedAt` was not read — the claim above is that the SPEC has no case for it, which rests on that file read in full, plus this firing's own tool response. Which way the implementation actually branches is still open and would settle in one reading by anyone who can open that file.

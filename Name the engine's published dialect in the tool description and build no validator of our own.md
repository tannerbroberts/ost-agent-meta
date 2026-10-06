---
type: Solution
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: assertion
killIf: >-
  A caller hits an unsupported-construct refusal on a surface whose description
  already named that construct as absent.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A caller reads a tool's stated dialect before composing against it]]

**Variation dimension: bought-vs-built. Position: the dialect definition is adopted from outside, verbatim; the only thing built here is the pointer to it.** The sibling candidates build something — a structured query compiler, a pattern parser. This one builds nothing that can drift, on the argument that the engine's own maintainers already publish an exact syntax reference and any second description of it is a copy that will disagree with the engine before it disagrees with itself.

The tool's description states which engine it is — "patterns are RE2 syntax as implemented by ripgrep; look-around and backreferences are not present" — and links the upstream reference. The caller reads the boundary before composing rather than after failing, which is the thing neither other candidate delivers.

**What is bought, precisely.** The enumeration of what the dialect does and does not contain, maintained by people who change the engine when they change it. What is built here is one sentence and one URL.

**What it gives up.** It is prose, so nothing enforces that it stays true: an engine swap or a version bump can make the description wrong with no test going red, and a description that disagrees with its own validator is a failure mode this tree already holds a separate node about. It also assumes the caller reads the description before composing, which is an assumption about behavior and not a mechanism — and that assumption is the one worth testing first, because if callers do not read it, this candidate delivers nothing at all while costing almost nothing.

**Cheapest of the three by a wide margin**, which is the argument for trying it first even though it is the weakest guarantee.

## Provenance

Ideated by an unattended sweep on 2026-09-03 against the assigned variation dimension `bought-vs-built`. Rests on the parent opportunity's evidence and on nothing else. The upstream reference was not fetched — this pass did not spend a web lookup to confirm the published syntax page still exists, so that is an open check for whoever picks this up.

## Definition of done — and it is not a command

"Add the dialect sentence, then count unsupported-construct refusals over the following twenty sessions"

No command, on purpose. The bar is **unsupported-construct refusals fall by at least half, and no more than 1 refusal names a construct the sentence already listed**. The counting half could be mechanised off the friction records; the deciding half cannot, because separating "the description had a gap" from "the description went unread" requires reading each surviving refusal against the sentence, and both produce an identical exit code.

Note the asymmetry a reader should not miss: the build here is one sentence, so this candidate is cheap to try and expensive to evaluate — the reverse of its two siblings. That argues for shipping it first and running this test alongside the others rather than before them.

The test title is quoted rather than wikilinked: its one backlink belongs to its parent assumption.

## 2026-09-09 — the tool has two dialects, and this candidate's one sentence covers one of them

Four lines. Not a restatement: this is a scope correction to the candidate, from a record captured by this firing's own ingest.

**What was observed.** `TRANSCRIPT:8116d697-1362-4c37-8552-c0b7782cb224` (3 events, harvested 2026-09-09T07:05Z) carries a `Grep` refusal that is *not* the look-around case this node was ideated from: `rg: error parsing glob '{Widen': unclosed alternate group; missing '}' (maybe escape '{' with '[{]'?)`. The rejected construct is brace alternation in the **glob** argument, not a regex construct in the pattern. The tool's own error text names three inputs it can reject — "ripgrep rejected the pattern, glob, or file type without searching" — so the surface already distinguishes them.

**Why that costs this candidate something specific.** Its bought half is "the enumeration of what the dialect does and does not contain", delivered as one sentence naming the regex engine — "patterns are RE2 syntax as implemented by ripgrep; look-around and backreferences are not present". That sentence, shipped exactly as written, would not have prevented this refusal: a caller who read it and believed it would still have composed the same glob. Ripgrep publishes glob syntax and regex syntax as separate references, so "one sentence and one URL" is under-specified at the count — the cheapest honest form of this candidate is one clause per rejectable input, and the pointer is at least two URLs rather than one. That raises its build cost slightly and, more importantly, makes its give-up worse: a description that enumerates one dialect while the tool rejects on three is not merely unenforced prose, it is prose a reader can follow correctly and still be refused.

**What it does not change.** The parent belief — whether a caller reads a stated dialect before composing — is untouched, and this record is weak evidence about it in the unhelpful direction only (one refusal is not a reading rate). The humans-required Definition of done above stands unchanged, and the asymmetry it names (cheap to build, expensive to evaluate) is unaffected. The counting half of that test should now count refusals **per rejected input**, or a halving driven entirely by the regex clause will read as the whole sentence working.

**Limits.** One record, one refusal, one session — this establishes that a second dialect is rejectable on this tool, not how often. The claim that ripgrep documents glob and regex syntax separately is stated from the error text's own three-way distinction and general knowledge of the tool, not from a fetched page; the upstream reference was not read, and the Provenance section's open check on that URL is now an open check on two. Nothing was executed, no instrument was set, no rung moved, no status changed, no node created. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.

_Method: `ost_next_work({evidence})` read of one record captured by this firing's own `ost_ingest_inbox`. Observed behaviour of the surface this agent runs on; it grounds usability, not desirability._

## Issues
- 2026-09-17 2026-09-17 unattended sweep (repo sight held): examined for a missing instrument and deliberately left without one. Recording the examination because this node appears in `solutionsMissingInstruments` and, unlike its neighbours in that bucket, carried no prior census note — so each firing has re-derived the verdict from the body.

The verdict, which this node's own Definition of done already states: humans-required, not un-done. Its single test, "A caller reads a tool's stated dialect before composing against it", asks whether callers read a description before composing. A spec could assert that the description string contains the dialect clause — that is a fact about our own text — and it would say nothing about the belief, which is about reading behaviour. This node's DoD names the same asymmetry precisely: the counting half is mechanisable, the deciding half is not, because "the description had a gap" and "the description went unread" produce an identical exit code. The tree already carries the matching ask on its standing queue: "Add the dialect sentence, then count unsupported-construct refusals over the following twenty sessions".

What would move it: a human sets the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on the unattended surface. Note for whoever does: the 2026-09-09 section above widens the bar — refusals should be counted per rejected input (pattern, glob, file type), not in aggregate, or a halving driven entirely by the regex clause will read as the whole sentence working.

Nothing else changed — no instrument set, no status changed, no rung moved, no node created. `ost_check` is withheld here, so this write is unverified by the invariant checker by design.

## 2026-10-04 — a second glob-brace refusal, in a different session

The 2026-09-09 section rested its scope correction on one record and said so ("One record, one refusal, one session"). Here is a second: `TRANSCRIPT:09834cbb-e5a0-4559-9f83-2959a2b2ddcb` (2026-09-28, unattended) holds `rg: error parsing glob '{A': unclosed alternate group`, which is the same construct (brace alternation in the **glob** argument) composed independently about three weeks later. That makes two sessions, so the miss is not a one-off. It is still too few to give a rate. If the one-sentence form ships covering only the regex dialect, this is the refusal it would let through.

_Method: one evidence body read via `ost_next_work({evidence})`. Observed behaviour of this agent's own surface; it grounds usability, not desirability. Nothing executed, no instrument set, no rung moved. `ost_check` is withheld on this surface, so this write has not been verified by the invariant checker._

## 2026-10-06 — the glob refusals are not the engine's dialect: the wrapper splits on whitespace, and a reference page would have called the input valid

A third session with the same refusal arrived this firing: `TRANSCRIPT:7c1e84c1-8247-43f3-9de0-2a1f880b2b53` (2026-10-06, unattended) has two of them, `'{A'` and `'*{evidence'`. With three independent sessions it is clearly not a one-off. What is new is that this firing reproduced the refusal directly instead of reading about it, and the cause turned out not to be the one this node's 2026-09-09 section assumed.

**What was run, first-party, against this vault's `.ost-agent/` directory with the harness's own `Grep` tool:**
- glob `*.{jsonl,md}`: **searched**, and it found the evidence file. Brace alternation is accepted.
- glob `*.{jsonl}`: **searched**, and it returned no files (a correct empty answer, not a refusal).
- glob `*{evidence, x}*`: **refused**, with `rg: error parsing glob '*{evidence': unclosed alternate group`. That is the same error text as the harvested record.

**What that shows.** Ripgrep parses brace groups fine. The fragment it rejects is exactly the input cut at the first space, so the `Grep` wrapper splits its `glob` argument on whitespace before it reaches ripgrep. Each half then reaches ripgrep as its own malformed glob. The construct the caller wrote is the one ripgrep's published glob syntax permits. The input broke on the way to ripgrep.

**What this costs this candidate.** The bought half was "the enumeration of what the dialect does and does not contain, maintained by people who change the engine". For this class of refusal, that enumeration would answer *valid*. A caller who read the upstream reference carefully would compose `{evidence, x}` and still be refused. So the 2026-09-09 correction ("one clause per rejectable input, and the pointer is at least two URLs") does not go far enough. Upstream documentation cannot describe a constraint the wrapper adds, so the sentence this candidate needs would have to be *built here*: something like "the glob argument is split on whitespace; do not put spaces inside a brace group". That undercuts the bought-vs-built position the candidate was ideated to occupy. The constraint is also owned by the harness (Claude Code's `Grep` tool), not by this product, so this product's tool descriptions are not where the sentence would live.

**What it does not change.** Whether callers read a stated dialect before composing is still the open belief, and nothing here bears on it. The regex-pattern half of the original evidence (look-around, backreferences) is a genuine engine-dialect limit and is unaffected. The humans-required Definition of done stands. Its per-input counting should now also separate *engine* refusals from *wrapper* refusals, because only the first can be fixed by pointing at the engine.

**Limits.** Three probes in one session, against one directory. "Splits on whitespace" is the simplest reading consistent with the fragment the error printed. Other separators were not tested, and the harness source was not read. Nothing was recorded as a result, no instrument was set, and no rung moved. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.

_Method: one evidence body read via `ost_next_work({evidence})`, plus three `Grep` calls by this firing that reproduced the refusal. This is observed behaviour of this agent's own surface. It grounds feasibility and usability, not desirability._

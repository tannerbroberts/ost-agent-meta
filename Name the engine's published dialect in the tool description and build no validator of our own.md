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

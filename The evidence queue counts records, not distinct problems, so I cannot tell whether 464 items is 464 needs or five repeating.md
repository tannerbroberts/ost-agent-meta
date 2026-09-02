---
type: Opportunity
source: 'TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11'
created: '2026-08-30'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Group the queue by error signature at read time, and change nothing on disk]]
[[Signatures extracted automatically, the decision that two errors are one problem left to the operator]]
[[Adopt the age-out mechanism already built here and widen only its redundancy predicate to count uncited repeats]]

**The need, from the operator's side.** `unmappedEvidence` reports a number — 441, 445, 457, 464 across the last four sweeps — and that number is the only thing an operator has to judge how far behind discovery is. It counts *records*. It does not say how many distinct problems those records describe. An operator reading 464 cannot tell whether that is 464 needs waiting to be distilled or a handful of failures repeating several hundred times, and those two readings call for opposite actions: the first is a staffing problem, the second is a deduplication problem.

**What was observed, first-party, on 2026-08-30.** Six evidence bodies were read in full out of the 25-record head. Their 61 `tool_error` events do not describe 61 problems. They cluster into five repeating failure modes:

- `File has not been read yet. Read it first before writing to it.` — in `134bad7e` (Edit and Write) and `09ec7cd2` (Write ×2).
- Module resolution against an unbuilt or wrongly-rooted checkout — `Cannot find module './src/security/tools.js'` in `134bad7e`; `Cannot find module './scripts/provenance-census.js'` and an `ERR_MODULE_NOT_FOUND` in `09ec7cd2`.
- A withheld capability discovered by calling it — `030e5db3` burns four calls learning it lacks `ost_flag_humans_required`, `ost_check`, `ost_status` and a repo read grant; `08f7d98f` burns two on the same `Glob` grant.
- A composite shell command refused by `Monitor` — `134bad7e` ×2, the second a near-identical re-composition of the first.
- A transient upstream outage — GitHub GraphQL `HTTP 503` ×3 in `09ec7cd2`, which is not a product defect at all.

Five modes across six records. The tail is not visible from this surface, but nothing in the head suggests the ratio improves.

**Why this is a need and not a restatement of the noise problem.** The tree already carries a branch on records that are *entirely* self-manufactured — the loop's own prescribed no-argument calls — measured this same pass at 12% of the head. This node is about the other 88%: records whose contents are genuine friction, which still cannot be worked one at a time because they say the same five things. Suppressing procedure does not touch it. A solution that filters the loop's own calls would serve that branch and leave this one exactly where it is, which is the test for whether these are two opportunities or one.

**Litmus test (more than one way to address this?).** Yes, and they differ in who bears the cost: cluster records by error signature at harvest and file one record per signature with a count; leave records intact but report a distinct-signature figure beside the record count so the denominator is honest; enable the existing age-out rule, whose implemented condition is age *and* redundancy with an already-cited signature; deduplicate at ingest so the second instance of a signature never becomes a record. Passes.

**What this node does not claim.** It does not say records should be discarded — a repeating failure repeating is itself information, and the count of instances is part of the finding. It says the queue presents that information in the one shape an operator cannot act on. Nor does it propose which of the four routes is right; that is ideation, and none has happened here.

**Provenance and rung.** Six transcript bodies plus the sweep response that listed them, all from this vault's own unattended firings — `observed`, being a mechanical recording of the agent's own usage. It grounds usability, not desirability: it is evidence that the surface is hard to work with, not evidence that anyone outside this project wants it fixed. No test was run and no result is recorded.

## 2026-08-30 — the same question asked of all 500 records instead of six, and the answer holds

The section above answers this node's question on six bodies read from the head of the queue, and says plainly that the tail is not visible from that surface. It is visible by grep. This pass counted every `TRANSCRIPT_*.md` record the vault holds, so the ratio the six-record sample suggested now has a corpus behind it.

**The corpus.** 500 transcript records (474 of them still unmapped). **1,195 `tool_error` events** across 426 records, and **815 `retry` events** across 384 — 2,010 friction events in all.

**Eight signatures account for two-thirds of every tool error in the corpus.** Shares are of the 1,195; the second figure is how many distinct records carry the signature.

| Signature | Events | Share | Records |
|---|---|---|---|
| `File has not been read yet` | 416 | 34.8% | 221 |
| `requested permissions to read from <path>` | 130 | 10.9% | 110 |
| `requested permissions to use mcp__…` | 91 | 7.6% | 29 |
| `No such file or directory` | 63 | 5.3% | 55 |
| `InputValidationError` | 46 | 3.8% | 38 |
| `String to replace not found in file` | 21 | 1.8% | 17 |
| `Monitor` refusing a composite command | 8 | 0.7% | 4 |
| tool exists but is not enabled in this context | 8 | 0.7% | 7 |
| **these eight together** | **783** | **65.5%** | — |

**What that settles.** The reading this node put as its second option — a handful of failures repeating several hundred times — is the one the corpus supports, and by a wider margin than the six-record sample could show. One signature is a third of everything. Two permission signatures together are another 18.5%, and the withheld-tool one is remarkable for its shape: 91 events across just 29 records, so it is not a common failure but a concentrated one, which is this node's point in miniature — a queue counting records ranks it eighth, a queue counting problems ranks it third.

**The honest limit, stated as a number rather than a caveat.** The eight leave **412 events (34.5%) untriaged**. Nothing here shows that remainder is diverse; it was simply not grepped for, and a longer signature list would very likely absorb more of it. So 65.5% is a floor on the concentration, not an estimate of it, and the direction of the error is known: further counting can only make the queue look more repetitive, never less.

**One figure that bears on the sibling branch rather than this one.** Retries are 815 of the 2,010 friction events — **40.6%** — and the branch on self-manufactured records establishes that the bulk of those are the loop's own prescribed no-argument pair. That is consistent with the 12% whole-record figure recorded there and does not overlap this count, which is confined to `tool_error`.

**What this does not settle, and it is the thing that decides between the four routes.** Signature identity is not problem identity. `No such file or directory` at 63 events is one string covering many unrelated missing files, while `File has not been read yet` at 416 is plausibly one problem — and no grep can tell those apart, because deciding that two errors are the same problem is a judgement. That is exactly the split the candidate "Signatures extracted automatically, the decision that two errors are one problem left to the operator" draws, and this census is evidence for the extraction half being cheap and mechanical, not for the judgement half being automatable.

_Method: greps of every `TRANSCRIPT_*.md` in this vault's evidence folder, counted corpus-wide, 2026-08-30. Observed behaviour of this product's own agent, captured mechanically with no narrator; it grounds usability, not demand. The records counted stay listed as unmapped evidence — counting them does not map them. No test was run, no result recorded, and this node's rung is unchanged._

## 2026-09-01 (later firing) — two records arrived this firing, and neither carries a need this tree lacks

Kept short. This is a small addition to the corpus counts above, not another census.

**What arrived.** `ost_ingest_inbox` captured exactly 2 new records this firing, both from the transcript channel, taking the unmapped queue from 557 to 559. Eight of the nine configured channels returned nothing or are disabled. Both were read in full.

**What they contain, against the eight signatures counted on 2026-08-30.** `5b14c137` is two events: a failing `Bash` test run and one "File has not been read yet" — the latter is the corpus's single largest signature. `82c427bd` is five: a `Glob` refused with "Claude requested permissions to read from /Users/tanner/dev/OST-Agent, but you haven't granted it yet", a `Glob` refused for an unexpected `head_limit` parameter, a `Grep` refused because ripgrep does not support look-around, and two no-argument retries of `ost_ingest_inbox` and `ost_next_work`.

**Every one of those is already mapped.** The permission refusal is the subject of "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time", and a grep of this vault finds that signature in roughly 140 stored transcript records — it is not a new arrival, it is one of the commonest. The read-before-write error is the largest counted signature and is held by "The file changed after I read it, and the failed edit is how I find out". The two schema refusals are the subject of "Publish each tool's accepted grammar in its own description, so the refusal is never provoked". The no-argument retries are the loop's own prescribed call pair, already counted and already mapped.

**So: 2 records in, 0 new needs.** That is consistent with the corpus finding above and adds nothing to it except a fresh interval. Deliberately no opportunity was created: each of these records maps to a need the tree already states, and `source:` is a single field, so "mapping" them would mean minting duplicate opportunities whose only function is to decrement a counter.

**One first-party corroboration this pass can add that a count cannot.** The permission refusal in `82c427bd` was not merely read this firing — it was *reproduced* by this firing, on the same path, in the same shape: a built-in `Glob` at `/Users/tanner/dev/OST-Agent` was refused for want of a grant, while `ost_read_repo` read the identical checkout without complaint, because `product.repos` sanctions it. Recorded on the node that holds that need rather than restated here.

_Method: `ost_ingest_inbox`, two evidence bodies via `ost_next_work({evidence})`, one grep over this vault's stored transcript records, and one reproduction observed in this firing's own tool results. Observed behaviour of this product's own agent; it grounds usability, not demand. The two records stay listed as unmapped — reading them does not map them._

## 2026-09-01 — correction to the pointer in the section immediately above

Three lines. The section above ends "Recorded on the node that holds that need rather than restated here." It was not, and the reason is worth one sentence rather than leaving a reader hunting for a section that does not exist.

The node that holds it — "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time" — carries a standing instruction to future passes in its own body: *do not append another sighting*, because a `Glob` denial on the product path with `ost_read_repo` answering normally against the same directory is the established default and confirms nothing new; add a census row only when a number moves. This firing's reproduction is that default exactly, its prompt-versus-withheld-list disagreement is already recorded there as confirmed first-party on 2026-09-01, and no number moved. So the sighting was deliberately not filed, and the pointer above should be read as "already established elsewhere", not "written up elsewhere".

_No node changed as a result of this reproduction. Correction recorded during the same 2026-09-01 unattended sweep that made the claim._

## 2026-09-02 — the number series gets its first arrival *rate*, and it is small

Kept short, per this node's convention. Only what is new: every count on this node so far is a snapshot of the queue's *composition*. None is a rate. This firing has two dated snapshots a day apart and can state one.

**The series, extended.** This node opens with "441, 445, 457, 464 across the last four sweeps". A 2026-08-31 section counted 534 transcript records on disk against 508 reported unmapped; a 2026-09-01 firing recorded the queue moving 557 → 559 at its own ingest. This firing's stop condition, computed before it ingested anything, read **562**; its `ost_ingest_inbox` captured exactly 1 new record, taking it to **563**.

**So: +4 in roughly 24 hours, of which this firing supplied 1.** That is the first figure on this node with time in the denominator, and it is much smaller than the growth this node's neighbours reason about. The queue is not filling fast. It is failing to drain — 563 items, 0 retired, against an arrival rate of a handful a day.

**What the single arrival contained, read in full.** `TRANSCRIPT:59dce6e4-2115-458d-819e-af5885cfc62b`, mirrored 0d ago: **2 events, both `retry`, both no-argument — `ost_ingest_inbox` and `ost_next_work`.** No `tool_error`. That is the pure self-manufactured shape exactly, at 1 of 1 for this batch, and it is a fifth consecutive forward confirmation of the generator rather than a retrospective count. **New needs distilled: zero.** Deliberately no Opportunity was created — the record's entire contents are this loop obeying its own step 1 and step 5, and `source:` is a single field, so "mapping" it would mint a duplicate whose only function is to decrement a counter.

**One inference the rate permits, and it cuts against a claim on the sibling branch.** Every firing that follows the prescribed loop files a record, because the no-argument pair is guaranteed to trip the repeat detector and `fetchSince` only skips a session with *no* events. So the arrival count is a lower bound on the firing count: ~4 arrivals in a day implies about that many firings, not dozens. The manifest branch's "the backlog grows fastest when nothing is wrong" is directionally right and quantitatively tiny — suppression at harvest would save this queue roughly one record a day.

**Limits, stated so this is not over-read.** Two snapshots is not a trend, and the interval is approximate: the 559 figure comes from another firing's prose rather than from a timestamped ledger, and neither reading fixes an hour. Transcript harvesting may lag a session's end, so arrivals in a 24-hour window need not correspond to firings in that window — the lower-bound inference is sound in aggregate and unreliable over one day. Nothing here re-counts composition; the 65.5% signature concentration and the 14.2% whole-record noise figure are untouched and were not re-derived.

_Method: this firing's own stop-condition figure, its `ost_ingest_inbox` output, and one evidence body via `ost_next_work({evidence})`. Observed behaviour of this product's own agent, captured mechanically — it grounds usability, not demand. The record stays listed as unmapped; reading it does not map it. Nothing executed, no rung moved, no instrument set, no status changed, no node created._

## 2026-09-02 (later firing) — the untriaged third is not diverse either, and the arrival rate recorded this morning was three times too low

Kept short, per this node's convention. Two things only, both first-party, both corrections to numbers already on this node rather than a new census.

**1. Three more repeating signatures inside the "untriaged 34.5%".** The 2026-08-30 section names its own honest limit: eight signatures cover 65.5% of tool errors, "the eight leave 412 events (34.5%) untriaged", and "nothing here shows that remainder is diverse; it was simply not grepped for". This firing grepped for three strings that list does not cover, over today's corpus of **602** transcript records:

| Signature not on the eight-row list | Occurrences | Records |
|---|---|---|
| `Blocked:` — a guard refusing a Bash or Monitor command | 35 | 32 |
| `Cannot find module` / `ERR_MODULE_NOT_FOUND` | 27 | 24 |
| A test suite reporting failures (`Tests N failed`) | 20 | 20 |

The first row matters most as a correction. The eight-row table counts "`Monitor` refusing a composite command" at **8 events across 4 records** — the narrowest reading of that failure. The guard's actual refusal string appears **35 times across 32 records**, so that row was undercounting its own signature roughly four-fold, and the shortfall sits in the untriaged remainder exactly as that section predicted.

**What this settles and what it does not.** It confirms the stated direction of the earlier error — "further counting can only make the queue look more repetitive, never less" — with three named signatures rather than an assurance. It does **not** restate 65.5% as a higher number, and deliberately so: these counts are over 602 records where the 65.5% was computed over 500, and this grep does not separate a string appearing in a `tool_error` body from the same string inside a `retry` payload, which the earlier event counts did. So the three rows are a floor on what the remainder contains, on a different denominator, and are not arithmetic on the old one.

**2. The arrival rate.** The 2026-09-02 section immediately above states "+4 in roughly 24 hours", concludes "the queue is not filling fast", and infers that harvest-side suppression "would save this queue roughly one record a day". That firing read a stop condition of 562 and ingested 1, reaching 563. **This firing, the same calendar day, read a stop condition of 574 and ingested 2, reaching 576.** So the queue moved 562 → 576 — **+14 in one day, of which 11 arrived from sessions that were neither firing.** The rate is about three and a half times the figure recorded this morning, and the "one record a day" saving attributed to suppression is understated by roughly the same factor.

**Which of that morning's claims survive.** Its structural inference stands and is strengthened: arrivals are a lower bound on firings, and 11 unattributed arrivals in a day means more sessions are running than either firing could see. Its conclusion does not — "the queue is not filling fast" rested on a two-point series whose own limits paragraph said "two snapshots is not a trend", and the third point broke it. The drain is still the larger problem: **576 items, 0 retired**, and nothing here changes that.

**One figure re-read on a moved corpus.** Records containing `retry` events and **no** `tool_error` at all: **94 of 602 (15.6%)**, against the 14.2% whole-record noise figure recorded earlier. Same phenomenon, slightly larger share.

_Method: three greps over every `TRANSCRIPT_*.md` in this vault's evidence folder, plus this firing's own stop-condition figure and `ost_ingest_inbox` output. Observed behaviour of this product's own agent, captured mechanically — it grounds usability, not demand. The records counted stay listed as unmapped; counting them does not map them. Nothing executed, no rung moved, no instrument set, no status changed, no node created._

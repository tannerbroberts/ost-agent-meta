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

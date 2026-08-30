---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A reader shown five signature groups acts on the groups instead of asking for the records behind them]]

**Variation dimension: who-does-the-work. Position taken: the agent, at read time — and nobody edits, stores, or curates anything.**

`ost_next_work` keeps returning what it returns, but adds a grouping computed fresh each pass: the unmapped queue rendered as distinct error signatures with a count and one representative record each. "463 records, 5 distinct signatures — module-not-found ×N, file-not-read-first ×N, capability-not-granted ×N, composite-command-refused ×N, upstream-5xx ×N." Nothing is written, nothing is suppressed, nothing collapses, and no artifact needs maintaining by anyone.

**Why this position and not another.** The sibling positions put the work on the operator (a curated fold) or on stored machinery (a widened age-out predicate). This one puts it on the reading agent and lets it evaporate afterwards. The queue's defect is a presentation defect — the information needed to group is already in the records, and every pass already reads a page of them. Nothing has to be decided or persisted for a reader to stop mistaking 463 for a workload.

**What it deliberately does not do.** It builds no suppression, no dedup, no store change, and takes no view on which signatures matter. A grouping is not a judgement about importance, and this candidate makes none — it reports the shape and leaves prioritisation where it lives, with the operator.

**What it gives up, plainly.** The store still grows at the same rate, so this fixes the reading and not the accumulation; an operator who cares about disk or ingest cost gets nothing. The grouping is recomputed every pass, so the cost is paid forever rather than once. And because nothing is recorded, there is no audit trail of what got grouped with what — a signature scheme that merges two genuinely different problems does so invisibly, and the next pass repeats the error with no memory that it made it. The siblings both leave a trace; this one leaves none. It is the cheapest answer to legibility and the weakest answer to accumulation.

**Cheapest form.** Normalise each friction event to `toolName + errorTextWithVolatileFieldsStripped`, group the unmapped set on it, and emit the groups alongside the existing `shown`/`total`/`hidden` counters — so a reader can tell a queue of five problems from a queue of 463 without opening a record.

**Honest note on how this was ideated.** The sweep asked for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.

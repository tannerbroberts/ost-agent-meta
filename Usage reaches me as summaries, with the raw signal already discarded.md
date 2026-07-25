---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
---
#Opportunity #unvalidated #needs-customer-interview #founder-theory
[[Raw-first telemetry store with summaries as derived views]]
[[Operator-owned local event log with consented raw export]]
[[Backpressure-tolerant ingest channel that preserves provenance under load]]

**The need (customer's voice):** "I want everything that happened when someone used this — every call, every retry, every place they stopped — not a rollup that somebody already decided was the interesting part. The moment it's summarised, the thing I didn't know to ask about is gone."

**Why it matters:** The outcome asks for both *quantity* and *believability* of non-founder data about usage. A summary is a derived artifact: it inherits whoever wrote the aggregation's idea of what mattered, and it cannot be re-interrogated when the question changes. Raw usage sits on the `observed` rung; a rollup of it does not. The founder's phrasing was explicit — "I want all of it, not just the summaries" — and he named the hard part himself: building input channels that can absorb that influx *and keep it all straight* is an engineering problem in its own right, not a switch to flip.

**Litmus test (is this an opportunity, not a solution?):** Many distinct ways to address it — a full-fidelity event log with summaries as derived views, an operator-owned local store that exports raw on consent, session replay reconstructed from the append-only journal, sampling that retains raw for the sampled slice, harvesting transcripts. Passes.

**Relationship to parent:** A proper subset. The parent concerns whether any outside signal exists at all; this concerns the *fidelity* at which it arrives. Solving the parent while keeping this unsolved yields outside data already flattened into someone else's summary — more inputs, no more answerable questions.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

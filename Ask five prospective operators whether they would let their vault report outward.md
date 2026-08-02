---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: desirability**, in its sharpest form — not "would they like it" but "would they permit it."

**The assumption under test.** That operators running their own OST-Agent would let it report their vault's activity back to a central inbox the founder reads. Every downstream benefit of this candidate — cross-instance learning, ideation from aggregate experience — is conditional on consent, and consent is being assumed rather than asked. If operators refuse, the candidate does not shrink; it dies, and the fallback is a fundamentally different design (local-only learning, or aggregate counts with no content).

**Why this is the riskiest assumption here and not the plumbing.** The plumbing is known-feasible: this vault already ingests from four channels including its own transcripts. Nothing about a fifth remote channel is technically hard. What is unknown is whether a PM will point a tool at their live product strategy and let it phone home — the content of an OST vault is competitive positioning, unshipped roadmap, and candid internal criticism.

**The test (five conversations, no build).** Five prospective operators. Show them a real, populated vault — this one, or a redacted copy — and the exact payload the reporting channel would send. Ask past-behaviour questions rather than intent questions: *what other tools have you turned telemetry off in, and what made you do it?* Then the direct one: would you run this with reporting on, off, or not at all? Record the answer and the reason verbatim.

**Pre-committed threshold.** **3 of 5 accept full content reporting** and the candidate stands as designed. **Fewer than 3, but 3 or more accept metadata-only** (counts, node totals, no bodies) and the candidate survives in reduced form and should be rewritten to match. **Fewer than 3 for either** and it is closed.

**Blocked on, and honestly so.** This test needs five people who are not the founder, which is the whole of [[I can't tell if anyone outside my own head wants this]] — the tree's own designated target row. It cannot jump that queue, and recording it here is not a claim that it can. It is filed so the design exists the day the queue clears.

**Who runs it.** A human, in conversation. Never compute.

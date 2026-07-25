---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Risk category: Viability.** Riskiest assumption: the freshness lag and sync overhead of a local read-only mirror are acceptable trade-offs for the extra isolation (vs reading live systems).

**Proposed test (small, fast):** For one project, build the tree from a mirror and from live reads; compare quality/latency, and ask operators the maximum staleness they'd tolerate.

**Pre-committed success threshold:** tree quality unaffected and the required sync lag falls within operators' stated acceptable staleness.

_Proposal only — a human runs this. Unvalidated._

---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test is mirror staleness acceptable versus live reads]]

**Candidate solution (unvalidated).** A separate sync step maintains a local read replica/export of the relevant source-system data; the agent reads only from that mirror and never holds live, write-capable credentials during a maintenance pass.

**Approach:** *air-gap the agent from live systems*.

**Contrast with siblings:** read-only tokens and secret-isolation still let the agent touch live APIs; this removes live access from the agent's runtime entirely, at the cost of sync freshness/complexity.

_Addresses: "Connecting my systems of record could leak or corrupt them". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

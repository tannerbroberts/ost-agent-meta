---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[A mirror can be stale and still be good enough to read discovery evidence from]]

**Candidate solution (unvalidated).** A separate sync step maintains a local read replica/export of the relevant source-system data; the agent reads only from that mirror and never holds live, write-capable credentials during a maintenance pass.

**Approach:** *air-gap the agent from live systems*.

**Contrast with siblings:** read-only tokens and secret-isolation still let the agent touch live APIs; this removes live access from the agent's runtime entirely, at the cost of sync freshness/complexity.

_Addresses: "Connecting my systems of record could leak or corrupt them". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Test is mirror staleness acceptable versus live reads]] — moved under [[A mirror can be stale and still be good enough to read discovery evidence from]] — the belief this test measures now has a node of its own

## Definition of done

[[Test is mirror staleness acceptable versus live reads]]

```
npx vitest run test/adapters/mirror-staleness.test.ts
```

Green means: staleness is a number the mirror reports rather than a property nobody can see — every record carries its fetch time, reads return the age with the data, and anything past the configured bound is served explicitly marked stale. Green does **not** say the staleness is acceptable; that depends on what a team is deciding with the data and is a person's call.

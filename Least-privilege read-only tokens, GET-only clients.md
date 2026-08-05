---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Read-only access is enough to gather the evidence the tree needs]]

**Candidate solution (unvalidated).** Each integration authenticates itself with a least-privilege, read-only API token supplied via environment variable and issues only GET requests against the vendor's cloud REST APIs. The agent structurally cannot write back to the system of record.

**Approach:** *minimize privilege at the API boundary* (read-only, GET-only).

**Contrast with siblings:** unlike secret-isolation (protects the credential) this constrains what the credential can do; unlike a local mirror it still touches the live system, but only reads.

_Addresses: "Connecting my systems of record could leak or corrupt them". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Test is read-only GET access enough to gather needed evidence]] — moved under [[Read-only access is enough to gather the evidence the tree needs]] — the belief this test measures now has a node of its own

## Definition of done

[[Test is read-only GET access enough to gather needed evidence]]

```
npx vitest run test/adapters/get-only-client.test.ts
```

Green means: every adapter request in a full ingest is a GET, and a non-GET verb is refused by the client itself rather than by the remote's permissions — so an over-scoped token cannot hide a violation. Green does **not** mean GET-only is *sufficient*; whether a real project's evidence is fully retrievable read-only needs a real Jira/Confluence corpus and stays with a human.

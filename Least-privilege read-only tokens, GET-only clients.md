---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test is read-only GET access enough to gather needed evidence]]

**Candidate solution (unvalidated).** Each integration authenticates itself with a least-privilege, read-only API token supplied via environment variable and issues only GET requests against the vendor's cloud REST APIs. The agent structurally cannot write back to the system of record.

**Approach:** *minimize privilege at the API boundary* (read-only, GET-only).

**Contrast with siblings:** unlike secret-isolation (protects the credential) this constrains what the credential can do; unlike a local mirror it still touches the live system, but only reads.

_Addresses: "Connecting my systems of record could leak or corrupt them". Unvalidated — human to review._

---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test scan confirms no secret ever lands in vault or history]]

**Candidate solution (unvalidated).** Credentials live only in the environment / OS keychain and are never written into the vault, so they can't leak into git history, a synced remote, or the tree itself. Blast radius of a compromised vault excludes the tokens.

**Approach:** *isolate the secret from the artifact*.

**Contrast with siblings:** read-only tokens limit what a leaked credential can do; this prevents the leak surface entirely; a local mirror removes live credentials from the run path altogether.

_Addresses: "Connecting my systems of record could leak or corrupt them". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

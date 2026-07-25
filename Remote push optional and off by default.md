---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test do operators get value with remote push off]]

**Candidate solution (unvalidated).** Nothing leaves the operator's machine unless they explicitly enable and configure remote push. By default the vault is local-only, so the blast radius of any bad commit — or any prompt-injection — is confined to a local folder under version control.

**Approach:** *containment / minimize blast radius*.

**Contrast with siblings:** the other two address whether harm can happen or be undone locally; this bounds where its effects can propagate. Together they cover expression, recovery, and containment.

_Addresses: "Fear the agent could take a destructive, irreversible action". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test does git auto-init and one-command revert work everywhere]]

**Candidate solution (unvalidated).** The agent operates only on a git folder (instantiating git if absent) and only ever makes new commits — never force-pushes, rebases, or deletes history. The worst case is a nonsensical commit the operator reverts with one command.

**Approach:** *make harm reversible* — bound the worst case to the operator's tolerance line.

**Contrast with siblings:** unlike the append-only tool surface (harm can't be expressed) this assumes bad output can happen but guarantees recovery; complements it as defense-in-depth.

_Addresses: "Fear the agent could take a destructive, irreversible action". Unvalidated — human to review._

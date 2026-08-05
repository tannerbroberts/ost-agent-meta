---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Git auto-init and one-command revert work on the machines this will actually run on]]

**Candidate solution (unvalidated).** The agent operates only on a git folder (instantiating git if absent) and only ever makes new commits — never force-pushes, rebases, or deletes history. The worst case is a nonsensical commit the operator reverts with one command.

**Approach:** *make harm reversible* — bound the worst case to the operator's tolerance line.

**Contrast with siblings:** unlike the append-only tool surface (harm can't be expressed) this assumes bad output can happen but guarantees recovery; complements it as defense-in-depth.

_Addresses: "Fear the agent could take a destructive, irreversible action". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test does git auto-init and one-command revert work everywhere" — moved under "Git auto-init and one-command revert work on the machines this will actually run on" — the belief this test measures now has a node of its own

## Definition of done

"Test does git auto-init and one-command revert work everywhere"

```
npx vitest run test/git/revert-fidelity.test.ts
```

Red today because no spec snapshots, mutates, reverts and compares. The vault auto-commits and `test/git/` covers conflict and lock behaviour, so a write that silently escaped a commit, or a revert that left a file behind, would go unreported. Green means a pass in a fresh empty directory and a pass inside an existing repository both revert to a byte-identical prior tree in one command, and that auto-init produced a repository in the empty case rather than writing outside version control.

What it does not settle: the third environment this node names — a machine with no git preinstalled — is genuinely about somebody's laptop, and no exit code in this suite stands in for it. That half stays a person's check and should be recorded separately rather than read off this command.

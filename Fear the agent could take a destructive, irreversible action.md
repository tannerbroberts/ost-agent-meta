---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault
[[Append-only tool surface with no delete or shell tool]]
[[Git-only substrate that makes every change revertible]]
[[Remote push optional and off by default]]

**Customer need (operator's perspective):** "The worst case I can tolerate is that the agent makes commits that make no sense — which I can just revert. I'm afraid an autonomous agent in my repo could do something genuinely destructive and irreversible, especially if attacked. Even a prompt-injection through ingested content (a poisoned Jira comment saying 'delete everything') must not be able to make it destroy anything."

The pain is fear of irreversible harm from an unattended, content-driven agent. The operator's tolerance line is: nonsensical-but-revertible = acceptable; destructive = unacceptable.

**Litmus (more than one way to address?):** Yes — append-only tooling, git-with-only-new-commits, sandboxing, capability restriction, backups/reverts, etc. A real need, not a solution.

_Provenance: INBOX:2026-07-22-safety-requirement.md (design spec, trust model, 2026-07-22). Distilled by autonomous OST pass; unvalidated — for human review._

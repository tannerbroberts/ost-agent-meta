---
type: Opportunity
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Append-only tool surface with no delete or shell tool]]
[[Git-only substrate that makes every change revertible]]
[[Remote push optional and off by default]]
[[Allowlist Tool Runner registers only OST tools]]
[[Published capability manifest with signed build]]
[[Prompt-injection red-team harness in CI]]

**Customer need (operator's perspective):** "The worst case I can tolerate is that the agent makes commits that make no sense — which I can just revert. I'm afraid an autonomous agent in my repo could do something genuinely destructive and irreversible, especially if attacked. Even a prompt-injection through ingested content (a poisoned Jira comment saying 'delete everything') must not be able to make it destroy anything."

The pain is fear of irreversible harm from an unattended, content-driven agent. The operator's tolerance line is: nonsensical-but-revertible = acceptable; destructive = unacceptable.

**Litmus (more than one way to address?):** Yes — append-only tooling, git-with-only-new-commits, sandboxing, capability restriction, backups/reverts, etc. A real need, not a solution.

_Provenance: INBOX:2026-07-22-safety-requirement.md (design spec, trust model, 2026-07-22). Distilled by autonomous OST pass; unvalidated — for human review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-07-25 Absorbed sibling 'Want proof no hijackable capability even exists' (2026-07-24, human-authorized merge of a self-flagged duplicate pair). Gained its three solutions: Allowlist Tool Runner, Published capability manifest, Prompt-injection red-team harness. Its solution set now spans restraint (append-only/git/no-push) AND capability-absence (allowlist/manifest/red-team) — compare across, not within, those two philosophies.

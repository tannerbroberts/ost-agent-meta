---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Append-only tool surface with no delete or shell tool]]
[[Git-only substrate that makes every change revertible]]
[[Remote push optional and off by default]]
[[Prompt-injection red-team harness in CI]]

**Customer need (operator's perspective):** "The worst case I can tolerate is that the agent makes commits that make no sense — which I can just revert. I'm afraid an autonomous agent in my repo could do something genuinely destructive and irreversible, especially if attacked. Even a prompt-injection through ingested content (a poisoned Jira comment saying 'delete everything') must not be able to make it destroy anything."

The pain is fear of irreversible harm from an unattended, content-driven agent. The operator's tolerance line is: nonsensical-but-revertible = acceptable; destructive = unacceptable.

**Litmus (more than one way to address?):** Yes — append-only tooling, git-with-only-new-commits, sandboxing, capability restriction, backups/reverts, etc. A real need, not a solution.

_Provenance: INBOX:2026-07-22-safety-requirement.md (design spec, trust model, 2026-07-22). Distilled by autonomous OST pass; unvalidated — for human review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Allowlist Tool Runner registers only OST tools]] — this solution is assurance-from-absence — it registers only the OST tools so no general-purpose or destructive capability exists to hijack, which is that opportunity's need almost verbatim, and its litmus already names an allowlist-only tool runner as one of the ways to meet it — one node, one parent
- 2026-08-05 unlinked [[Published capability manifest with signed build]] — this solution publishes the exact tool list as an inspectable, signed manifest — it is proof about which capabilities exist, which is the assurance-from-absence need; it constrains no destructive action on its own — one node, one parent

## Issues
- 2026-07-25 Absorbed sibling 'Want proof no hijackable capability even exists' (2026-07-24, human-authorized merge of a self-flagged duplicate pair). Gained its three solutions: Allowlist Tool Runner, Published capability manifest, Prompt-injection red-team harness. Its solution set now spans restraint (append-only/git/no-push) AND capability-absence (allowlist/manifest/red-team) — compare across, not within, those two philosophies.

## Realized instance (mapped 2026-07-25)

`INBOX:2026-07-25-friction-an-empty-annotation-is-recorded-rather-than-refu.md` — the fear materialized in inverted form: not deletion but permanent garbage. ost_annotate accepted an undefined issue string and wrote literal `undefined` into the tetrix-ost root's append-only history twice; the damage is permanent and the intent unrecoverable. The need extends to write-time refusal of degenerate input: an append-only design makes *bad writes* as irreversible as deletions would be.

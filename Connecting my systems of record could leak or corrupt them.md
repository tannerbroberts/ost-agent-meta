---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault
[[Least-privilege read-only tokens, GET-only clients]]
[[Local read-only mirror of source systems]]
[[Secrets never stored in the vault]]

**Customer need (operator's perspective):** "I want to connect my systems of record (Jira, Confluence, etc.) so the agent can learn from them — but I'm worried about credential blast radius and about the agent writing back to and corrupting my source-of-truth systems. My credentials must not be exposed, and it must never write to those systems."

The pain is two-fold fear when integrating external systems: (1) credential exposure/over-scope, and (2) unwanted write-back to systems of record. This gates whether operators are willing to connect real data at all.

**Litmus (more than one way to address?):** Yes — least-privilege read-only tokens, GET-only clients, never storing secrets in the vault, OAuth scoping, proxies, local mirrors, etc.

_Provenance: INBOX:2026-07-22-adapter-reality.md (implementation note, Atlassian adapter, 2026-07-22). The evidence describes one implementation; reframed to the underlying operator need. Distilled by autonomous OST pass; unvalidated — for human review._

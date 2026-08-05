---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[An adversarial suite catches the injection attacks that would actually be attempted]]

**Candidate solution (unvalidated).** Every build runs an adversarial suite of poisoned-content cases (e.g. ingested notes instructing "delete everything", "exfiltrate the token") and asserts that no tool call outside the allowlist ever fires. Capability-safety is proven continuously, not once.

**Approach:** *adversarial verification / regression proof*.

**Contrast with siblings:** the allowlist runner and manifest describe static capability; this demonstrates the system withstands active attack over time.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Test does the red-team harness catch known injection attacks]] — moved under [[An adversarial suite catches the injection attacks that would actually be attempted]] — the belief this test measures now has a node of its own

## Definition of done

[[Test does the red-team harness catch known injection attacks]]

```
npx vitest run test/security/injection-red-team.test.ts
```

Red today because neither the corpus nor the harness exists — `test/security/` holds an allowlist-registration audit and nothing else drives hostile ingested content through the reader. Green means all twenty seeded attacks are flagged **and** the mutation control goes red when the defence is removed. The mutation half is not decoration: it is the only thing separating a harness that catches attacks from one that catches nothing and reports twenty passes.

What it does not settle: twenty attacks somebody thought of is not the attack surface. A green here says the known twenty are caught, never that the twenty-first is, and nothing about it is evidence that an operator would trust the product more for having it.

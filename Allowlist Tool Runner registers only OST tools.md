---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Trust can rest on absence of capability, with no general-purpose tool ever registered]]

**Candidate solution (unvalidated).** Use the Anthropic API SDK Tool Runner, which registers *only* the tools we define, instead of the Claude Agent SDK, whose built-in Bash/Write/Edit tools would have to be disabled by blocklist. No general-purpose or destructive tool exists to hijack — trust from absence of capability, not restraint of a capable agent.

**Approach:** *allowlist by construction* — the dangerous tool never enters the runtime.

**Contrast with siblings:** unlike a published manifest (proves what's there) or a red-team harness (proves it resists attack) this is the underlying mechanism that makes those claims true.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Test audit that no tool outside the allowlist is ever registered]] — moved under [[Trust can rest on absence of capability, with no general-purpose tool ever registered]] — the belief this test measures now has a node of its own

## Definition of done

[[Test audit that no tool outside the allowlist is ever registered]]

```
npx vitest run test/security/allowlist-registration-audit.test.ts
```

Green means every tool the runner registers is on the declared allowlist, checked against the registration path rather than against a reading of it. This is a containment property and the audit is the right shape for it. It does not settle whether the allowlisted tools are themselves safe in combination — an audit that everything present was permitted says nothing about what permitted things can do together.

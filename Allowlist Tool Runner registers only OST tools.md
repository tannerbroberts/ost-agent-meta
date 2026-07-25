---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test audit that no tool outside the allowlist is ever registered]]

**Candidate solution (unvalidated).** Use the Anthropic API SDK Tool Runner, which registers *only* the tools we define, instead of the Claude Agent SDK, whose built-in Bash/Write/Edit tools would have to be disabled by blocklist. No general-purpose or destructive tool exists to hijack — trust from absence of capability, not restraint of a capable agent.

**Approach:** *allowlist by construction* — the dangerous tool never enters the runtime.

**Contrast with siblings:** unlike a published manifest (proves what's there) or a red-team harness (proves it resists attack) this is the underlying mechanism that makes those claims true.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

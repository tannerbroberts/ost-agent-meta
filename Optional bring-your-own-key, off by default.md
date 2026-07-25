---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test can users complete first run without providing a key]]

**Candidate solution (unvalidated).** Default operation requires no key (ambient agent). Power users who want fully headless scheduled runs may optionally supply their own API key — strictly opt-in, never required to try or to run interactively.

**Approach:** *make the credential optional and additive*, not a gate to entry.

**Contrast with siblings:** unlike ambient-only it enables unattended cron for those who want it; unlike a bundled model it defers to the user's chosen provider/quality.

_Addresses: "Don't want to buy a second AI credential just to try it". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

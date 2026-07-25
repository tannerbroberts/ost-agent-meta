---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test can users complete first run without providing a key]]

**Candidate solution (unvalidated).** Default operation requires no key (ambient agent). Power users who want fully headless scheduled runs may optionally supply their own API key — strictly opt-in, never required to try or to run interactively.

**Approach:** *make the credential optional and additive*, not a gate to entry.

**Contrast with siblings:** unlike ambient-only it enables unattended cron for those who want it; unlike a bundled model it defers to the user's chosen provider/quality.

_Addresses: "Don't want to buy a second AI credential just to try it". Unvalidated — human to review._

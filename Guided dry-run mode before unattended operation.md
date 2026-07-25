---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test does a supervised dry run raise willingness to enable cron]]

**Candidate solution (unvalidated).** Before enabling scheduled unattended runs, the operator runs a bounded, observable first pass on their real evidence and watches what the agent produces. Confidence is earned interactively; only then do they grant cron/headless operation.

**Approach:** trust via *progressive onboarding — earn confidence before walking away*.

**Contrast with siblings:** unlike the audit trail and digest (which build trust during/after unattended runs) this front-loads trust-building into a supervised trial.

_Addresses: "Trust an unmonitored agent enough to walk away". Unvalidated — human to review._

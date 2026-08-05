---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test does a supervised dry run raise willingness to enable cron]]

**Candidate solution (unvalidated).** Before enabling scheduled unattended runs, the operator runs a bounded, observable first pass on their real evidence and watches what the agent produces. Confidence is earned interactively; only then do they grant cron/headless operation.

**Approach:** trust via *progressive onboarding — earn confidence before walking away*.

**Contrast with siblings:** unlike the audit trail and digest (which build trust during/after unattended runs) this front-loads trust-building into a supervised trial.

_Addresses: "Trust an unmonitored agent enough to walk away". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Definition of done

[[Test does a supervised dry run raise willingness to enable cron]]

```
npx vitest run test/loop/dry-run-no-writes.test.ts
```

Green means: a full pass under the dry-run flag produces its usual plan and report while git HEAD is unchanged and no node file is touched. Green does **not** mean anyone is more willing to enable cron — that half is a person's reaction and stays with a human.

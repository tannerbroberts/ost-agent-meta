---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md'
created: '2026-08-02'
evidence: stated
---
#Opportunity #unvalidated #evidence/stated

Same vault, same instant, two versions of the tool: one reported 9 items outstanding, the other 27. Nothing about the vault had changed. The newer build decided done-ness by reading a state ledger the older one never wrote, so every item mapped under the old accounting silently re-opened as unfinished work.

The cost is not only the wasted passes. It is that the record of what has been done is not a property of the vault, it is a property of whichever version last looked at it — and the vault gives no sign that its history has been reinterpreted. Work that was genuinely finished now reads as outstanding, and there is no way to tell that class of item apart from work that really is.

**The need:** I want what I have already finished to stay finished across an upgrade, or at minimum to be told when an upgrade has changed the answer.

More than one way to address this: migrate the old accounting into the new ledger on first run, keep reading the legacy signal as a fallback, refuse to run against a vault written by an incompatible version until a migration is acknowledged, or report the accounting change explicitly instead of folding it into the counts.

## Provenance

Distilled from `INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md` — filed by the twenty-passes ambient driver comparing ost-agent@0.1.3 against a HEAD build on the same vault.

---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Migrate the old accounting into the new ledger on first run, and record that it happened]]
[[Keep reading the legacy signal as a fallback so old work still counts]]

Same vault, same instant, two versions of the tool: one reported 9 items outstanding, the other 27. Nothing about the vault had changed. The newer build decided done-ness by reading a state ledger the older one never wrote, so every item mapped under the old accounting silently re-opened as unfinished work.

The cost is not only the wasted passes. It is that the record of what has been done is not a property of the vault, it is a property of whichever version last looked at it — and the vault gives no sign that its history has been reinterpreted. Work that was genuinely finished now reads as outstanding, and there is no way to tell that class of item apart from work that really is.

**The need:** I want what I have already finished to stay finished across an upgrade, or at minimum to be told when an upgrade has changed the answer.

More than one way to address this: migrate the old accounting into the new ledger on first run, keep reading the legacy signal as a fallback, refuse to run against a vault written by an incompatible version until a migration is acknowledged, or report the accounting change explicitly instead of folding it into the counts.

## Provenance

Distilled from `INBOX:2026-07-25-friction-upgrading-the-cli-silently-reopened-18-mapped-ev.md` — filed by the twenty-passes ambient driver comparing ost-agent@0.1.3 against a HEAD build on the same vault.

## History
- 2026-08-02 evidence: stated → assertion — Demoted from 'stated' for consistency: rests on an inbox friction note, and the inbox channel's earned ceiling is 'assertion'.

## Issues
- 2026-08-02 Live instance of this opportunity observed during the 2026-08-02 pass, worth a human's eye because it is the same mechanism this node describes, still active. `.ost-agent/state/mapped.json` lists TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18 and TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1 among its mapped ids, yet `ost_next_work` reported both as unmapped evidence in the same minute. Two records therefore sit in the ledger as done and in the counter as outstanding at once. Neither was mapped by this pass. Separately and consistently with the same root cause: appending a corroborating section to an existing node does NOT add that evidence id to the ledger — only `ost_create_node` with a `source` does — so reusing an existing opportunity, which the ruleset explicitly prefers over duplicating, leaves the evidence permanently counted as unmapped. That is a structural pressure toward creating a duplicate node rather than reusing the right one, pushing against the rule it is meant to serve.
- 2026-08-02 Duplicate of a prior disposition — flagged by the pass that created it, 2026-08-02. The Outcome's ledger for the twenty-passes cycle 2 (2026-07-25) records "version-skew doneness friction → MAPPED: appended to 'The pass never says it is done…' (mechanism 2)". The same evidence is therefore already represented on that node as one of its mechanisms, and this pass created a separate opportunity for it because the append left the item counted as unmapped — the exact effect that ledger entry predicted in its own closing note. A human should decide whether the mechanism belongs where it was first appended or as this standalone node; keeping both means one piece of evidence is represented twice.

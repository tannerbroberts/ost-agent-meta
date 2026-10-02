---
type: Assumption
source: 'agent-ideation:2026-10-01-unattended-sweep'
created: '2026-10-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[next_work emits unmapped friction grouped by signature, collapsing records that differ only in volatile fields]]

**Kind: feasibility.**

The belief: every unmapped `TRANSCRIPT:` friction record already carries enough to group on — a tool name and an error line — so `ost_next_work` can compute `toolName + error text with volatile fields stripped` at read time and emit the groups next to `shown`/`total`/`hidden`, with no new stored field and no second read.

**How it could be false.** The records could be too varied for a stripping rule to collapse (paths, session ids and permission targets differ in every line, as in `TRANSCRIPT:030e5db3-9414-441f-9221-b4a984c11825`, where four denials name four different targets), so the "five signatures" turn out to be eighty. Or the record body as stored could lose the tool name, so grouping needs the original transcript.

**Why it is the one to test first.** The sibling assumption ("A reader shown five signature groups acts on the groups instead of asking for the records behind them") is about whether the operator trusts the groups. That question is only worth an operator's afternoon if the groups exist and are few. This one the repository can answer.

Unvalidated. Agent-surfaced 2026-10-01; a human to review.

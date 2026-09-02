---
type: Assumption
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Category: feasibility.**

The belief, stated so it could be false: a `tool_use` block in a Claude Code transcript carries a caller-written field other than the command itself — the Bash tool's `description` — and that field is still present in the JSONL the harvester reads, so `extractFriction` can pair it with the `tool_result` that follows.

**Why it could be false, concretely.** `extractFriction` today stores `{ name, input }` in `toolById` and nothing else, and `input` is the whole block input serialised. If the description does not survive into the persisted transcript, or arrives on a different entry from the one carrying the tool-use id, the caller has nowhere to write a mark that the harvester can read, and the candidate above has no cheapest form — it needs a transcript change, which is the host's, not this product's.

**What settles it and what it leaves alone.** A spec against the adapter settles whether the field can be threaded through and honoured. It settles nothing about whether an agent will actually write the mark, which is this candidate's larger risk and is recorded on the solution's kill condition instead.

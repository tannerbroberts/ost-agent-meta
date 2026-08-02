---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-opp-transcript-ingestion.md'
created: '2026-07-24'
evidence: assertion
---
#Opportunity #unvalidated #needs-customer-interview #evidence/assertion
[[Post-session transcript harvester]]
[[In-the-moment friction events filed by the agent]]
[[Mine tool errors and retries from run logs]]
[[The friction that matters leaves no error behind]]

**The need (customer's voice):** "The agent gets confused, asks the same question again, stalls on the same step — and all of that is thrown away when the session ends. The clearest usage data this product has ever produced is being deleted every day."

**Why it matters:** A subset of the evidence-famine need, addressing a channel that already exists and is currently discarded. The agent running the OST is the product's most active user; every question, uncertainty, retry, and stall it hits is *observed behavior* (non-founder, non-stated) about where the product is hard to use. Unlike recruiting outside users, this channel needs no one's permission.

**Litmus test:** More than one way — harvest transcripts into the inbox, emit structured friction events at the point of stall, have the agent file its own confusions, mine commit/tool-error history. Passes.

**Caveat for a human:** Dogfood friction is usage data about *one* user who is not a paying customer, so it grounds usability far better than it grounds demand. It should not be allowed to substitute for the outside-user evidence the parent opportunity is about.

Evidence: `INBOX:2026-07-24-opp-transcript-ingestion.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-07-25 Mis-parent flag (2026-07-24 review): the node's own caveat concedes dogfood friction must not substitute for the outside-user evidence its parent ('I can't tell if anyone outside my own head wants this') is about — a child that explicitly does not deliver the parent's need. Proposed reparent to an evidence-channel/instrumentation row; human to confirm.

## Evidence — eleven session traces and three usage rollups (mapped 2026-08-02)

Captured mechanically by the transcript and usage channels, covering 2026-07-25 to 2026-07-31. Recorded here rather than distilled into new opportunities: individually these are builder-toolchain slips, not unmet needs. What makes them evidence for *this* node is that they repeat across independent sessions and nothing carried the lesson from one to the next.

**Transcript channel — 11 sessions, 40 friction events.** `TRANSCRIPT:` ids `08ab58d6`, `424486ec`, `470cb94a`, `516fdfb8`, `87a025f8`, `97546e2f`, `a615eb46`, `b7aae32d`, `e335a680`, `f48dc76d`, `fd2c6d71`. Two patterns dominate and both are pure repetition:

- **zsh quoting — `(eval):1: == not found`, 9 occurrences across at least two sessions** (`a615eb46` ×5, `b7aae32d` ×3+). The same malformed comparison, retried unchanged, in sessions that never saw each other's failure.
- **`Blocked: sleep N followed by gh pr checks …`, 5 occurrences across 4 sessions** (`470cb94a`, `516fdfb8`, `a615eb46`, `b7aae32d`, `e335a680`). Each time the harness answered with the same correction — use an until-loop, or run in background — and each subsequent session made the identical call again.

The remainder are one-offs that carry no cross-session lesson: TypeScript errors mid-refactor (`e335a680`, `b7aae32d`), `Edit` old_string mismatches (`424486ec`, `516fdfb8`), a Workflow script written in TypeScript instead of JavaScript (`516fdfb8`), a 2-minute Bash timeout on a polling loop (`f48dc76d`), a `CronList` retry (`fd2c6d71`).

**Usage channel — 3 daily rollups, 217 calls.** `USAGE:2026-07-25` (108 calls, 0 failed, 3 sessions, p50 3ms), `USAGE:2026-07-26` (93 calls, **62 failed**), `USAGE:2026-07-27` (16 calls, 0 failed). The 2026-07-26 spike is the one number worth a human's eye: 75 of that day's 93 calls were `ost_annotate`, and the sampled failures are `no such node: probe` / `no such node: x` — a session probing the tool surface with throwaway node names, plus one `ost_create_node` refused for a literal `"undefined"` evidence class. That last one corroborates [[A tool call I got slightly wrong destroyed the note I was filing]] and the guard that now refuses it.

**What this does and does not support.** It is `observed`-rung on the agent's own behaviour and grounds usability only — per each record's own header, it is explicitly not outside-user demand data and must not be counted toward [[I can't tell if anyone outside my own head wants this]]. The claim it does support is this node's: a repeated, mechanically-visible failure mode existed in nine sessions and no session started better-informed than the last.

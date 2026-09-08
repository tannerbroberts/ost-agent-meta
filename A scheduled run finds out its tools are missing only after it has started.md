---
type: Opportunity
status: unvalidated
source: >-
  INBOX:friction/2026-08-01-friction-third-straight-scheduled-pass-15th-16th-17th-wit.md
created: '2026-08-02'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Declare the tool surface a pass requires and abort in the first second if it is absent]]
[[Have the scheduler verify the environment before it dispatches a run at all]]
[[Fall back to the command-line path automatically when the MCP tools are absent]]

Three scheduled passes ran in a session where the vault's tools were simply absent, so mapping, ideation and ranking could not run at all — only the command line remained. The run started, discovered its surface was empty, and each pass had to work that out for itself after the compute had already been committed.

The scheduling is the aggravating factor. An interactive session that loses its tools has a person present who sees it immediately; a scheduled one repeats the same discovery on a cadence, and the only record that anything went wrong is whatever the pass thought to file. Three identical passes is three identical discoveries and no accumulating signal.

**The need:** I want a scheduled run to know before it starts whether it can do the work it was scheduled for.

More than one way to address this: assert the required surface as a precondition and exit loudly, have the scheduler verify the environment before dispatching, fall back to the command-line path automatically when the tools are absent, or escalate after the first toolless run rather than the fourth.

## Provenance

Distilled from `INBOX:friction/2026-08-01-friction-third-straight-scheduled-pass-15th-16th-17th-wit.md` — filed by the session on the third consecutive toolless scheduled pass. Its root cause was located a day later and is mapped under a sibling opportunity. Recorded at `assertion`: the inbox channel's earned ceiling.

## Corroborating session (2026-08-04)

- `TRANSCRIPT:ac007b7b-ac18-4a19-94f1-cb5f3c93ca42` — `exit 127 … tmux not found`. The run had already begun and had already spent calls before the binary it depended on turned out not to be installed.
- `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f` — `exit 255 Undefined subroutine &main::pct`: a helper written for an interpreter that did not have the routine it assumed.

Both are the same shape as this need and both were discovered by execution rather than by a precondition check. `exit 127` is the cheapest possible signal to act on — it is unambiguous, it arrives from the shell rather than from a tool's own error handling, and it names the missing binary — which suggests a precondition sweep would not need to be clever to catch this class.

Evidence class is observed behaviour of this agent using its own harness — usability, not demand.

## 2026-09-07 — a sharper variant: the capability was present, only the route was wrong

Kept short. One new distinction, observed first-party by this firing rather than read off a record.

**The variant.** This node's prose is about a surface that is *absent* — three scheduled passes whose vault tools were simply not there. Two records and this firing's own behaviour show a second, cheaper-to-fix shape: the surface is present, the specific tool reached for is denied, and a tool that does the same job is granted on the same surface. Nothing says so, so the run finds out by spending a call.

**The records.** `TRANSCRIPT:030e5db3-9414-441f-9221-b4a984c11825` (2026-08-05) carries four denials in one nine-event session — `Glob` on `/Users/tanner/dev/OST-Agent/src`, and `ost_flag_humans_required`, `ost_check`, `ost_status`. `TRANSCRIPT:538b29d6-01cc-4e16-9846-09cc016a1fae` (2026-09-08, captured by this firing's own ingest) carries the same `Glob` denial on the repo root, one month later. Same class, two firings, no accumulating signal between them — which is exactly what the second paragraph of this node predicts.

**What this firing adds, and it is the part that is new.** This pass reproduced the `Glob` denial on `/Users/tanner/dev/OST-Agent`, then read the same repository successfully through `ost_read_repo` on the same surface, in the same pass. So repo sight was granted the whole time; the call that failed was a route to it that was not. That reframes at least part of this need: the loss is not always a missing capability, it is sometimes an unannounced mapping between what a pass reaches for and what it holds. A precondition check that only asserts "the surface is non-empty" would have passed cleanly on both records and saved nothing.

**Why it bears on the solutions already hanging here.** The three candidates beneath this node all assume the binary case — the tools are there or they are not. "Declare the tool surface a pass requires and abort in the first second if it is absent" would not fire here, because nothing required was absent. Whoever picks that candidate up should decide whether its declaration names capabilities (repo sight) or tool names (`Glob`), because those two readings behave differently on exactly these two records. No node created and no candidate ideated — this is a note for the human weighing them.

**Limits.** Two records, both this vault's own unattended firings plus this one: observed behaviour of the agent using its own harness, which grounds usability and is not evidence that anyone wants this built. The claim that `ost_read_repo` and `Glob` are substitutable is true for the read this pass actually needed (a directory listing and file bodies under `product.repos`) and is not a general equivalence. Nothing was executed, no rung moved, no status changed.

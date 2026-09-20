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

## Corroboration 2026-09-19 — TRANSCRIPT:b6784800-98b1-4dd9-b423-87f39c777240

An unattended firing tried to `Glob` the product repository (`/Users/tanner/dev/OST-Agent`) and was denied because the read permission had not been granted, which it only found out by making the call. Same actor as this node's other transcript sources (the agent's own sessions), so this adds a recurrence, not an independent voice. Rung unchanged.

## 2026-09-20 — the mapping is not merely unannounced, it is announced wrongly, in both directions

Kept short, per this branch's convention. This is not a fourth recurrence line and should not be read as one — `TRANSCRIPT:6b16e8af-c201-46d3-a528-88642c5f29ce`, captured by this firing's own ingest, carries the same `Glob` denial on `/Users/tanner/dev/OST-Agent` recorded here on 2026-09-19 and on 2026-09-07. Same class, same actor, one more time; that is persistence, and the corroboration line above already covers it.

**What the 2026-09-07 section established.** That the loss is "sometimes an unannounced mapping between what a pass reaches for and what it holds", and that a precondition check asserting only "the surface is non-empty" would have passed cleanly and saved nothing.

**The new fact: there is an announcement, and it is false in both directions.** This firing's own instructions state, under hard rules, that "this unattended sweep holds no outward-sensing grant on purpose" and that `ost_search_web` / `ost_read_web` / `ost_read_repo` "stay on the attended path". `ost_read_repo` was granted and this pass used it throughout — directory listings under `test/`, and full reads of `src/knowledge/instruments.ts`, `src/ost/red-now.ts` and `test/loop/wait-primitive-affordance.test.ts`. In the same prompt, the skill's "What this surface withholds" block names seven tools as denied (`ost_check`, `ost_debt`, `ost_deposit`, `ost_flag_humans_required`, `ost_gate`, `ost_rank_source`, `ost_status`), while the skill body above it describes the outward senses as available. So one document tells a pass that a granted tool is withheld, and tells it that some withheld tools are granted.

**Why that upgrades the finding rather than repeating it.** An unannounced mapping leaves a pass with no information and it spends a call to learn. A wrongly announced one leaves a pass with *negative* information: it either skips capability it holds, or reaches for the route it was told to use and draws the denial. This firing did both — it reached for `Glob` first, because the prompt had ruled the MCP route out, was denied, and only then tested `ost_read_repo` against the prompt's own claim and found it working. That is the likeliest explanation for why this denial recurs monthly from passes that all had repo sight available: they are not guessing, they are being told.

**What it changes about a fix.** The three candidates hanging here all sit at runtime, and the 2026-09-07 note asks whoever picks one up to decide whether the declaration names capabilities or tool names. This says the declaration itself is the defect, so a runtime check that reads it would inherit the error — a precondition sweep built from this prompt's grant list would assert that `ost_read_repo` is absent and that `ost_check` is present, and be wrong twice before the pass starts. The repair is upstream, in whatever generates the firing prompt and the skill's withheld block, and it is the same shape as the prompt-versus-validator contradiction recorded at length on "My instruments are red because a file is absent, not because the behaviour is": two artifacts describing one surface and disagreeing. No candidate ideated and no node created — this is a note for the human weighing them.

**The cost this pass paid, recorded because it is the cycle this vault already knows.** The `Glob` denial is a `tool_error`, the harvester files it, and the record joins `unmappedEvidence`, where it cannot be retired. This firing therefore manufactured one more queue record by following its own instructions — it is an instance of that cycle, not an observer of it.

**Limits.** The prompt text is this firing's own instructions read as given; a reader wanting to confirm it should check the loop's prompt template and the skill generator rather than take this node's word. The grant claim is first-party and observed — the calls succeeded — but "granted on this surface" is established for `ost_read_repo` only; the other two outward senses were never attempted, so whether they are also mis-declared is unknown. One firing, this vault's own unattended run: observed behaviour of the agent using its own harness, grounding usability, not demand. Nothing was executed, no rung moved, no instrument set, no status changed, no node created. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.

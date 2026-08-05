---
type: Opportunity
source: 'TRANSCRIPT:06eba571-9780-458a-b384-da5abe101e6f'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Non-interactive is the default, and any tool that would prompt is made to fail loudly instead]]
[[Settle the standing answers once, in committed configuration the run inherits]]
[[Detect that no terminal is attached and answer the prompt from a stated policy]]

When I hand work to a run that is meant to finish on its own, it does not fail — it stops, mid-command, at a question a tool asked expecting a human at a keyboard. Nothing about the stop announces itself as a stop. The run is simply still there, holding, until I happen to look.

The distinguishing thing is that this is not a decision I would want to be asked about. A tool defaulted to interactive because it could not tell nobody was watching. I would have answered every one of these the same way, every time, without thinking — which is exactly why being asked costs the whole run.

## What the evidence shows

- `TRANSCRIPT:06eba571-9780-458a-b384-da5abe101e6f` — `git` exits 128 with `hint: You have divergent branches and need to specify how to reconcile them. hint: You can do so by running one of the following …`. The reconcile policy is a one-time config; the run had no way to have set it.
- `TRANSCRIPT:e42cd03d-b2a4-44ba-989a-9e01cc368f77` — `overwrite src/web/budget.ts? (y/n [n]) not overwritten`. The prompt timed out to its default and the file was silently left alone; the command reported exit 1 rather than "I asked a question nobody heard."
- `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f` — a second `git` exit 128, `fatal:` truncated, in a directory listing that shows the repo was not where the command assumed.

## Why this is not the sibling need

The parent opportunity is about a loop that is genuinely blocked on a human decision and has no way to say so. This one is narrower and different in kind: there is no decision here at all. The correct answer was determined in advance in every case, and the stop is purely an artefact of a tool that could not detect it was running unattended.

Evidence class: observed behaviour of the agent's own usage, captured mechanically from session transcripts. It grounds usability, not desirability, and is not outside-user evidence of want.

## Corroborating sessions (2026-07-29 → 2026-08-04)

Six sessions stopped to ask a human a question. What the set shows is *what kind* of question: every one is a design judgement the run could have proposed a default for and carried on under.

- `TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866` — *"Should this turn ship the spec only, or also build the cheap ones?"* (scope).
- `TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc` — two: how a lineage prefix should clip long titles (format), and what should happen to the losing node when a pass judges two duplicates (semantics).
- `TRANSCRIPT:dcdaebdb-ffd9-4944-973b-cf0b8e1113c4` — which of two renderings to put in a script (format).
- `TRANSCRIPT:2c1b611a-ae7e-4191-aefe-b489c631a115` — how metacognition should sit relative to the external-returning-operators metric (framing).
- `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f` — which environment Vault 11 should be (configuration, with a Recommended option already identified).
- `TRANSCRIPT:87a025f8-c6b0-474f-9a13-0b5ec5c922ea` — one further clarifying question alongside a tool error.

Three of the six already carried a "(Recommended)" option, which means the run had a defensible default in hand and stopped anyway. That is the sharper version of this need: the blocker is not that the run lacks an answer, it is that it has no way to act on its own default and leave the question on the record.

Evidence class is observed behaviour of this agent using its own harness — usability, not demand.

## Eleven stops across nine sessions — and most of them had an answer ready

Every `clarifying_question` event captured in this vault's transcript channel, with what was being asked:

| Evidence | The question that stopped the run |
| --- | --- |
| `TRANSCRIPT:748498c4-…` | "Which environment should Vault 11 be?" — with a **(Recommended)** option |
| `TRANSCRIPT:470cb94a-…` | "Should this turn ship the spec only, or also build the cheap ones?" |
| `TRANSCRIPT:424486ec-…` | "Another process is writing to this repo right now… " |
| `TRANSCRIPT:87a025f8-…` | whether an obsolete PR #3 should be closed |
| `TRANSCRIPT:785ea509-…` | "How should the lineage prefix handle long node titles?" |
| `TRANSCRIPT:785ea509-…` | "When a pass judges two nodes to be duplicates, what should happen to the loser?" |
| `TRANSCRIPT:2c1b611a-…` | "How should metacognition sit relative to the external-returning-operators metric?" — with a **(Recommended)** option |
| `TRANSCRIPT:dcdaebdb-…` | "Which rendering should I put in the script?" |
| `TRANSCRIPT:9a406570-…` | "What does 'Print type' switch between?" |
| `TRANSCRIPT:9a406570-…` | "Should the GitHub repo be public or private?" |
| `TRANSCRIPT:35566d8b-…` | "What does 'Print type' switch between?" (same question, later session) |

**The observation that bears hardest on this node.** At least two of these stops shipped with the agent's own preferred option already marked *(Recommended)*. The run had a defensible answer, wrote it down, and stopped anyway. Whatever the right policy is, these are not cases where the run lacked a view — they are cases where having a view was not sufficient to continue, which is precisely the design question [[Bank each question, proceed on a stated default, and present the banked set at the end]] and [[A question queue the run banks and works around, instead of stopping at the fork]] are competing to answer.

**Not all of them are alike, and the node should not pretend otherwise.** "Should the GitHub repo be public or private?" is irreversible and outward-facing; "Which rendering should I put in the script?" is a formatting choice reversible in one edit. Any rule that defaults the second must not default the first — which is the sorting [[Sort the observed prompts into safe-to-default and must-stop, and see whether a rule separates them]] proposes, and this table is now the corpus it would run against.

**One event is worth more than the other ten.** In `TRANSCRIPT:785ea509-…` a `clarifying_question` is followed immediately by a `permission_denied` on the same tool: *"The user doesn't want to proceed with this tool use… the user said: The user wants to clarify…"*. The human rejected the question rather than answering it. That is not this node's complaint — a stop that a person is present for — it is [[Answering one question costs me three turns, because I have to fix its options before I can reply]], and it is the first machine-captured instance of it, recorded there.

_Provenance: eleven clarifying-question events across nine friction records from the transcript adapter, machine-captured, no narrator. Observed behavior of this product's own agent; grounds usability, not desirability. Unvalidated — for human review._

## Corroboration — eight further sessions, and what they were stopping to ask (2026-08-04 sweep)

Eight captured sessions each halted on `AskUserQuestion`. What is worth recording is not the count but the **kind** of question, because it bears on which candidate under this node could actually help.

Genuinely irreducible — a preference nobody but the operator holds:
- 9a406570 / 35566d8b (2026-08-04) — "Should the GitHub repo be public or private?"
- 748498c4 (2026-07-29) — "Which environment should Vault 11 be?"
- dcdaebdb (2026-08-04) — "Which rendering should I put in the script?"
- 9a406570 (2026-08-04) — "What does 'Print type' switch between?"

Answerable from state the run already had, or from a stated default:
- 470cb94a (2026-07-30) — "Should this turn ship the spec only, or also build the cheap ones?" — a scope question a standing policy could settle once.
- 785ea509 (2026-08-04) — "How should the lineage prefix handle long node titles?" — a formatting question.
- 785ea509 (2026-08-04) — "When a pass judges two nodes to be duplicates, what should happen to the loser?" — a policy question, since settled and built as `ost_merge_nodes`.
- 87a025f8 (2026-07-31) — "PR #3 is obsolete…" — a question that recites the full evidence for its own answer before asking it.
- 2c1b611a (2026-08-04) — "How should metacognition sit relative to the external-returning-operators metric?"

Roughly half are taste and half are policy. **A default-and-proceed mechanism only reaches the second half**, and the first half will stop an unattended run no matter how good the defaults are. Any candidate here that promises to eliminate blocking should be read against that split rather than against the raw count.

One further data point on the shape of the stop: in 785ea509 a question was itself refused (`permission_denied` on AskUserQuestion) with the operator saying they wanted to clarify — i.e. the options offered did not contain the answer. That is [[Answering one question costs me three turns, because I have to fix its options before I can reply]] happening inside a session already captured here.

_Recorded as corroboration during the 2026-08-04 unattended pass; these items remain unmapped in the sweep. Observed behavior, mechanically captured; grounds usability, not demand._

## A third kind of stop, and it is not a question at all (2026-08-05 sweep)

Every stop in this node's corpus so far is a *question* — `AskUserQuestion`, or a shell prompt waiting on a keystroke. `TRANSCRIPT:5de6e49b-d840-4fba-9549-206d3b0d7276` (2026-08-05) is the first captured instance of a different shape, and it is worth separating rather than adding to the count.

The single friction event is `ExitWorktree` refusing:

> *Worktree has 2 commits on `worktree-discovery-eyes`. Removing will discard this work permanently. Confirm with the user, then re-invoke with `discard_changes: true` — or use `action: "keep"` to preserve the worktree.*

Three things distinguish it from the eleven above.

**It is a refusal, not a question.** No option list was offered and nothing was waiting on an answer; the tool declined an irreversible act and named the two ways forward. The instruction to *confirm with the user* is the tool's, embedded in its own error text, which means the stop is a property of the surface rather than a choice the run made.

**It is correct.** Discarding two commits unprompted is precisely the action [[Fear the agent could take a destructive, irreversible action]] exists to prevent, and a mechanism that defaulted this one would be a defect. So this stop does not belong in either half of the taste/policy split recorded above — it is neither a preference only the operator holds nor a policy a standing default could settle. Defaulting it either way is wrong: `discard_changes: true` destroys work, and `action: "keep"` silently accumulates worktrees nobody prunes.

**What it wants is not a default but somewhere to put the work.** The run had produced two commits and could not put them down without a person. That is closer to [[A question queue the run banks and works around, instead of stopping at the fork]] than to [[Bank each question, proceed on a stated default, and present the banked set at the end]] — the run does not need an answer to continue, it needs the branch to survive unattended and be presented later. `action: "keep"` is arguably already that mechanism, and nothing told the run it was the unattended-safe choice.

**Consequence for reading this node.** Any candidate here that promises to eliminate blocking should now be read against a three-way split, not two: taste (irreducible), policy (defaultable), and *correct refusals* (must not be defaulted, and want a parking mechanism instead). The third category is the one where a default-and-proceed design does active harm, and it had no instance in the corpus until now.

_Source: `TRANSCRIPT:5de6e49b-…`, read in full this pass — the only one of the sweep's 18 unmapped items not already cited in some node's body. Observed behavior from the agent's own transcript; grounds usability, not demand. Corroboration only, and a new category rather than another tally mark; the node's rung is unchanged._

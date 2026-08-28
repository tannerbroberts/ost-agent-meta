---
type: Opportunity
status: unvalidated
source: 'human:conversation'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[The same agent has a different tool surface on every surface I run it on]]
[[Two thirds of my calls failed, and each one only told me after I made it]]
[[I probe for files that were never there, because nothing hands me the layout of the workspace I am in]]
[[I call a symbol I never wrote, and a whole-project typecheck at the end of the batch is what tells me]]
[[I run git in a folder that was never initialised, and exit 128 is how I learn it]]
[[I compose a hundred and seventy lines before the surface tells me it does not accept that dialect]]
[[Nothing declares what I have to work with, so every plan is built on a guess]]
[[Commands are composed against a repo layout nobody checked, so the first thing that runs is a path that isn't there]]
[[The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed]]
[[Every precondition is discovered by violating it, so a pass pays a turn per rule it did not know]]
[[A string I meant literally is read as syntax, so the command fails instead of searching]]
[[My instruments are red because a file is absent, not because the behaviour is]]

**The need (customer's voice):** "The OST-Agent shouldn't have to guess what its resources are." (Founder, verbatim, 2026-07-25.) The founder's own examples, kept in their words because each names a different resource class:
- "If a project is in the middle of a seed round, and has a million dollars it needs to spend intelligently, THAT'S WORTH KNOWING!!!" — capital, and its deployment deadline.
- "If a user isn't willing to talk to other people, that's a significant limitation." — the operator's social reach.
- "If the human in the loop doesn't want any part of it, know that." — human availability and appetite.
- "If the user WANTS to spend their token budget from an AI platform subscription as soon as the token limit reset time hits, that's an incredibly important functional constraint." — compute economics and its schedule.

**Why it matters:** Every plan the agent makes — which test to run, which solution to ideate, what to rank first and why — is implicitly conditioned on resources it was never told about. These are not subtle signals that must be inferred; they are *declarable facts the operator already knows* and would state if asked, and there is nowhere to put them. The founder flagged the prior framing directly: "I've previously mentioned 'getting to know its builder', but that's an understatement" — see "The agent has no picture of what the builder can do, because reasoning traces never reach it", which covers *inferring collaborator capability from traces*; this node covers *declared project resources and operating constraints*, a different mechanism (declaration vs. inference) and a different scope (the project's world, not one collaborator's skill).

**Observed cost of guessing, from this vault's own history (same day):** the cold-offer test was sequenced RUN FIRST on 2026-07-24 and declined by the founder on 2026-07-25 — "that isn't going to fly" — because it presupposed cold outreach the operator was never willing to do. A declared social-reach constraint would have redirected that planning before it was drafted. Likewise "I need the tree's output to be actionable by compute alone, because my hours don't exist" and "Every run ends blocked on a credential only I hold" are individual constraints of exactly this kind, each discovered the expensive way and each currently living as prose in an opportunity node rather than as a fact the planner consults.

**Direct dependency:** "Show me the whole priority order, and why each item sits where it does" — a priority ordering's "why" is only as good as the resource picture it's conditioned on. A project with a million dollars and a deadline ranks differently than one with zero human hours and a token-reset schedule; without declared resources, every rationale silently assumes some default operator.

**Litmus test:** More than one way — a declared resource/constraint manifest the operator fills in and amends (config-level, consulted by prioritization); an onboarding interview that elicits it; constraint fields carried on the Outcome node; budget-aware pass scheduling (the token-reset example is literally a scheduler input); periodic re-confirmation since resources change (a seed round closes, a human's appetite shifts). Distinct mechanisms, real trade-offs. Passes.

**Placement:** Top-level under the Outcome — it conditions planning across every branch rather than belonging to any one of them.

Evidence: founder statement in conversation, 2026-07-25.

## History
- 2026-07-25 evidence: (none) → assertion — founder-stated need, verbatim examples preserved; no external party involved; floor rung per the ladder's rule.
- 2026-08-05 unlinked "A declared resource manifest the planner must cite before it ranks anything" — re-parented under "Nothing declares what I have to work with, so every plan is built on a guess" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Constraint profile mined from what actually blocked the loop" — re-parented under "Nothing declares what I have to work with, so every plan is built on a guess" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Expiring resource questions asked at a fixed cadence" — re-parented under "Nothing declares what I have to work with, so every plan is built on a guess" — this solution answers that need, not the categories beside it

## Corroboration — session 0d27cebf (2026-08-02)

A mechanically-captured session produced 10 friction events, three of which are this opportunity happening in real time: `ls: /Users/tanner/dev/ost-benchmarks/bin/: No such file or directory`, `ls: /Users/tanner/dev/ost-agent-meta: No such file or directory`, and `cat: .gitignore: No such file or directory`. In each case the agent addressed a path it believed existed and learned otherwise from the shell's complaint.

The same session shows the cost compounding: a `tail` against a log file that had never been created, and a command that timed out after two minutes. None of these are reasoning failures — they are the absence of a reliable statement of what is actually on disk and where.

Source: `TRANSCRIPT:0d27cebf-9b5d-4cff-906c-0134512573bc` — observed behavior, captured from the agent's own transcript. Grounds usability, not demand.

## Corroboration — six further sessions, and the guessing is not only about paths (unattended sweep, 2026-08-03)

The Corroboration above rests on session `0d27cebf`. Five more sessions from the same eight-day window show the same behavior, and together they widen what "resources" means here.

**Paths guessed and refused** — `748498c4`: `sed: src/cli/index.ts: No such file or directory`, and a `git` command that came back `fatal:` against a directory it had just listed. `a0eb3fd4`: `cd:1: no such file or directory: docs/reference`. `5e5c119d` and `8fc8d6e3`, six days apart: `no matches found: /Users/tanner/dev/ost*` — the agent did not know where its own project lived.

**Symbols guessed and refused** — `e335a680` is the sharpest, because the compiler answered in the form this opportunity asks for: `error TS2552: Cannot find name 'reconcileWithUsage'. Did you mean 'reconcileWithGit'?`, and `error TS2339: Property 'configProblem' does not exist on type 'ToolContext'`. `b7aae32d` adds `The type 'readonly OstNode[]' is 'readonly' and cannot be assigned to the mutable type 'OstNode[]'`. The agent was composing against a remembered shape of its own codebase, not a declared one.

**The reconnaissance is visible too** — `a83f0269`'s single friction event is a directory listing of the whole `test/` tree, spilling `adapters cli config eval git knowledge loop mcp ost product release runner security skill smoke.test.ts telemetry web`. That is the manifest this node argues for, being reconstructed by hand, one failed call at a time.

The founder's framing was about capital, social reach, human appetite and token budget — resources an operator would *declare if asked*. These sessions show the same absence one layer down, in the resources the machine itself sits on: where the files are, what the symbols are, what the types permit. Same mechanism, same cost, and both are discovered the expensive way. Whether the manifest should cover both is a question for a human — recorded here rather than decided.

_Source: `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f`, `TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff`, `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18`, `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1`, `TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129`, `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd`, `TRANSCRIPT:a83f0269-c09e-45a3-a1f3-68f601b476c9` — observed behavior from the agent's own transcripts. Grounds usability, not demand._

## Corroboration — three more sessions guessing paths that were not there (unattended sweep, 2026-08-17)

`TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11` hit `Error: Cannot find module './scripts/provenance-census.js'` and `Error [ERR_MODULE_NOT_FOUND]: Cannot find module '/private/tmp/scripts/provenance-census.ts'` — a run composing against a script it believed existed. `TRANSCRIPT:0e0cd6f3-7541-4221-a6f1-efe977d0e2e2` hit `cat: test/product/offline-trial-pass.test.ts: No such file or directory` and `ls: src/automation: No such file or directory`. `TRANSCRIPT:19ccdb48-e5f7-4dda-8289-38b25a651397` hit `cat: test/mcp/edit-node-preserves-unsupplied-sections.test.ts: No such file or directory`. Same shape as the prior corroboration rounds: a path addressed as if declared, refused by the filesystem instead.

_Source: `TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11`, `TRANSCRIPT:0e0cd6f3-7541-4221-a6f1-efe977d0e2e2`, `TRANSCRIPT:19ccdb48-e5f7-4dda-8289-38b25a651397` — observed behavior, captured mechanically from the agent's own transcripts. Grounds usability, not desirability.

## Additional observed instances

TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11 — `Cannot find module './scripts/provenance-census.js'` and a second module-not-found error from a path under `/private/tmp/` that the session apparently assumed existed.
TRANSCRIPT:1c8a3722-b8a5-4828-b57e-c45b1566cf6d — a Read tool_error, "File does not exist," against a path the session guessed relative to the wrong current working directory (`/Users/tanner/ost-agent-meta` when the target was under `/Users/tanner/dev/OST-Agent`).

## Corroboration — a helper script's own import path, guessed and wrong (unattended sweep, 2026-08-18)

`TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8`: a `Bash` call failed with `Error [ERR_MODULE_NOT_FOUND]: Cannot find module '/private/tmp/src/ost/vault.js' imported from /private/tmp/check-queue.mts` — a build-loop monitoring script composed against a module path that does not exist at that location, the same shape as the earlier `e335a680`/`09ec7cd2` symbol- and module-path guesses already on record here, now against the loop's own tooling rather than the product's.

_Source: `TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8`, read in full this pass. Observed behavior; grounds usability, not demand. Corroboration only; the node's rung is unchanged._

## Issues
- 2026-08-26 2026-08-26 (second firing) — a new instance of this need, located in the *instruction text* rather than the tool surface. The unattended pass prompt contradicts itself about outward sensing: one paragraph states "Three read-only senses are now on this surface: `ost_search_web` and `ost_read_web` ... and `ost_read_repo`", and the "Hard rules" paragraph states "This unattended sweep holds no outward-sensing grant on purpose — `ost_search_web` / `ost_read_web` / `ost_read_repo` stay on the attended path". The skill's own "What this surface withholds" list, which is derived mechanically from the automation script, names six withheld tools and `ost_read_repo` is not among them. Resolved this pass by testing it: `ost_read_repo` served `test/` and `src/` on first call. So the hard-rules paragraph is wrong about `ost_read_repo`, and a pass that believed it would decline to read the repository and then report itself blind while holding a working read channel — which is exactly the failure "Every session leaves an evidence record that restates a need the tree already holds" records as the consequence of the within-session grant split, now reproduced in a second medium. The stated reason for the hard rule ("looking things up costs money") does apply to `ost_search_web` / `ost_read_web`, which this pass did not call; a local repo read costs nothing, which is likely why the two paragraphs disagree. For a human: reconciling the prompt against the script-derived withheld list is a one-line fix and would stop each firing rediscovering this by experiment. Grounds usability, not demand; no test was run and no result is recorded.

## The reflex probe confirms the wrong belief — two channels onto one resource, granted differently (unattended firing, 2026-08-28)

The 2026-08-26 Issues entry above records that the firing prompt contradicts itself about `ost_read_repo`, and that a pass believing the hard-rules paragraph "would decline to read the repository and then report itself blind while holding a working read channel". This firing hit that, and found a sharper version of it that the earlier note does not cover: **testing the belief is not enough, because the obvious test confirms it.**

What happened, in order. This pass read the hard-rules paragraph, provisionally accepted that it had no repo sight, and then went to check rather than assume — reaching for `Glob` on `/Users/tanner/dev/OST-Agent`, the reflex tool for "is this repository readable". It came back `Claude requested permissions to read from /Users/tanner/dev/OST-Agent, but you haven't granted it yet.` That is a **true refusal that licenses a false conclusion**: the harness file tools genuinely are not granted on the product path, so the probe is not a fluke and does not read like one. The pass wrote off the whole instruments bucket as ungroundable and was several calls into reporting itself blind before re-reading this node's own 2026-08-26 entry, which named the other channel. `ost_read_repo` then served `test/` on the first call, and the rest of the pass ran with full repo sight.

**The mechanism, stated generally, because it is not about these two tools.** One resource — the product's source — is reachable through two independently granted channels: the harness's own file tools and this product's MCP surface. The grants differ. Nothing anywhere enumerates them together, so an agent probing "can I read the repo?" is really probing "can I read the repo *this particular way?*" and gets an answer it will reasonably generalise. Every existing instance on this node is an agent guessing at a resource and being *corrected* by the failure; this is the first recorded instance where the failure **confirmed** the guess and the correction had to come from a note a previous pass left behind. A wrong answer that arrives as a clean, plausible refusal is strictly more expensive than one that arrives as an error, because nothing about it invites a second attempt.

**Why it belongs on this node rather than beside it.** The founder's framing here is resources an operator would declare if asked, and the extension already recorded is resources the machine sits on — where the files are, what the symbols are. This adds the dimension those both assume away: not *what* is there, but *which of my channels reaches it*. A manifest that answered "the product source is at /Users/tanner/dev/OST-Agent" would not have prevented this pass's error, because the path was never in doubt. What was in doubt was which grant applied, and that is a fact about the surface rather than about the workspace.

**For a human, and it is cheaper than the general fix.** The skill's "What this surface withholds" list is already derived mechanically from the automation script and is already correct — `ost_read_repo` is not on it. The prompt's hard-rules paragraph contradicts that list and is the thing sending each firing down this path; reconciling the two is the same one-line fix the 2026-08-26 entry asked for, now with a second, more expensive failure mode behind it.

_First-party to this firing, 2026-08-28: the `Glob` denial and the successful `ost_read_repo` call are both in this session's own record. Observed behaviour of the tool surface; grounds usability, not demand. No test was run, no result is recorded, and this node's rung is unchanged._

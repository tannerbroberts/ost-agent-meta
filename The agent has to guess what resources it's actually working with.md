---
type: Opportunity
status: unvalidated
source: 'human:conversation'
created: '2026-07-25'
evidence: assertion
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

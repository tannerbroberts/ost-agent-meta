---
type: Opportunity
source: 'TRANSCRIPT:e42cd03d-b2a4-44ba-989a-9e01cc368f77'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[A conflict marker cannot reach a commit, because the hook that would allow it refuses]]

Something resolved a merge badly and committed the result, conflict markers and all, into a source file. Whatever ran next did not inherit a disagreement to settle — it inherited a repository that does not compile, and had to stop and ask a human how the wreck should be cleaned up before it could begin the work it was actually started for.

## What the evidence shows

- `TRANSCRIPT:e42cd03d-b2a4-44ba-989a-9e01cc368f77` — a `clarifying_question` reading "How should the committed merge conflict in `src/cli/index.ts` be resolved?", alongside a second on how in-flight work "should land on the real origin/main". The conflict was already committed; the question is archaeology, not merge strategy.
- `TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab` — the live version of the same collision: two `Edit` failures with "String to replace not found in file", and then the discovery of why — "Another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago, including a brand-new `pushTargetFor` …)". The agent found out about the other writer only because its own edit missed.
- `TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129` — the downstream shape: `src/cli/index.ts(108,26): error TS2552: Cannot find name 'reconcileWithUsage'` and `src/security/tools.ts(744,63): error TS2339: Property 'configProblem' does not exist on type 'ToolContext'`. The same file, `src/cli/index.ts`, referencing a symbol that is not there.

## Why this is not just the parent need

The parent is about two agents overwriting each other's work in a vault. This is the state that outlives the collision: the trampling is over, both writers are gone, and what remains is a committed artefact that reads as a valid repository to everything except a compiler. Nothing on the way in refused it, so the cost lands on whoever arrives next.

## What I actually want

For a conflict marker to be unable to reach a commit, and failing that, for the run that inherits one to be told what it is inheriting before it starts planning work on top of it.

Evidence class: observed behaviour of the agent's own usage, captured mechanically from session transcripts. It grounds usability, not desirability, and is not outside-user evidence of want.

---
type: Opportunity
source: 'TRANSCRIPT:0d27cebf-9b5d-4cff-906c-0134512573bc'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Hand the run a layout of the workspace before it takes its first action]]
[[A failed path lookup answers with the nearest thing that does exist]]

I start work in a directory and immediately begin guessing at it — reaching for a path that sounds right, being told it does not exist, reaching for the next one. The guesses are not wild; they are the paths this project has had at some point, or has on another machine, or that a sibling project has. Nothing at the start of the run told me which of those is true here.

## What the evidence shows

- `TRANSCRIPT:0d27cebf-9b5d-4cff-906c-0134512573bc` — four separate misses in one session: `ls: /Users/tanner/dev/ost-benchmarks/bin/: No such file or directory`, `cat: .gitignore: No such file or directory`, `ls: /Users/tanner/dev/ost-agent-meta: No such file or directory`, and `tail: /Users/tanner/Library/Logs/ost-meta-loop.launchd.log: No such file or directory`.
- `TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff` — `(eval):cd:1: no such file or directory: docs/reference`.
- `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f` — `sed: src/cli/index.ts: No such file or directory`, followed by a listing showing the directory holds only `bin` and `vaults`.
- `TRANSCRIPT:a83f0269-c09e-45a3-a1f3-68f601b476c9` — an exit-1 whose output is a bare listing of the `test/` tree, the agent enumerating to find what it should have been handed.

Note the third one especially: `/Users/tanner/dev/ost-agent-meta` does not exist, but `/Users/tanner/ost-agent-meta` does. The guess was off by one path segment, and cost a call to learn.

## Why this is narrower than the parent

The parent is about resources in general — credentials, tool surfaces, budgets. This is specifically about filesystem layout, which is unusual among resources in that it is cheap to enumerate, completely knowable at the start of a run, and stable for its whole duration. It is the resource question with the most obvious answer and it is still being answered by trial.

Evidence class: observed behaviour of the agent's own usage, captured mechanically from session transcripts. It grounds usability, not desirability, and is not outside-user evidence of want.

---
type: Opportunity
source: 'TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129'
created: '2026-08-04'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Hand the run the project's symbol surface before it writes, not after it compiles]]
[[Typecheck the files just touched, at the moment they are touched]]

A run edits several files, then runs `npx tsc --noEmit` and learns that one of the edits referenced something that does not exist. The signal is correct and it is far too late: it arrives detached from the edit that caused it, after the rest of the batch has been written on top of the mistake.

Two captures, days apart, in the same shape:

- `TRANSCRIPT:e335a680-ee48-4171-b8ad-4cfb526e4129` — `src/cli/index.ts(108,26): error TS2552: Cannot find name 'reconcileWithUsage'. Did you mean 'reconcileWithGit'?` and, in the same session, `src/security/tools.ts(744,63): error TS2339: Property 'configProblem' does not exist on type 'ToolContext'`.
- `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd` — `The type 'readonly OstNode[]' is 'readonly' and cannot be assigned to the mutable type 'OstNode[]'`.

The `TS2552` is the most telling of the three, because the compiler supplies the answer — `Did you mean 'reconcileWithGit'?` — which means the correct name was recoverable from the project the whole time. The run did not lack the information; it lacked it *at the moment it was writing the call*. `configProblem` is the same story from the other direction: a property the run intended to add to `ToolContext` and referenced before adding.

Why this belongs under a resources-the-agent-cannot-see parent rather than under ordinary build failure: the missing thing is knowledge of the project's own symbol surface. The run is handed file contents on request and never handed what the project exports, what a type has on it, or what is mutable. It reconstructs that by writing a guess and reading the compiler's objection.

This is not a want-a-linter request, and it should not be narrowed into one before it has been sized. There is more than one way to meet it — hand the run an index of the symbol surface up front, check the touched files as they are touched instead of the project at the end, or let the run declare a symbol it intends to add so that calling it is a recorded intention rather than a break. Which is right depends on how often the class actually fires and how expensive each check is, and neither is known yet.

What this need does *not* claim: nothing here shows anyone outside this project has it. Both sources are this agent's own sessions, captured mechanically. It grounds usability of the build loop, not demand.

## Cost, as observed

Both sessions absorbed the failure and recovered within the same session, so the visible cost is turns rather than a broken deliverable. The unmeasured cost is the one worth sizing before anything is built: how many edits in a batch land on top of a symbol that was already wrong, and whether any of them had to be redone once the real name was known.

---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-27-friction-loop-step-records-the-command-and-its-exit-code-.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

A health record showed a build step exiting 1 against a command that passes cleanly in its intended directory. The command was run from the home directory instead of the repo, so the test runner collected four repositories at once and failed. The record captured the command and the exit code faithfully and said nothing about the one variable that explained the result.

What makes this expensive is that the record looks complete. There is no gap to notice, no missing field to chase — just a failure that cannot be reproduced and cannot be dismissed, which is the worst of both. Every such entry has to be re-run by hand before it can be believed, which is most of the value of having recorded it in the first place.

**The need:** I want a recorded failure to carry enough of its context that I can reproduce it without guessing what the environment was.

More than one way to address this: record the working directory and argv alongside the exit code, capture the resolved environment for any step that fails, refuse to record a step whose context is unknown, or replay the step in its recorded context on demand.

## Provenance

Distilled from `INBOX:2026-07-27-friction-loop-step-records-the-command-and-its-exit-code-.md` — filed by the loop after `loop step --phase build -- npx vitest run` was run from the wrong directory. Recorded at `assertion`: the inbox channel's earned ceiling, whatever the note says about itself.

---
type: Opportunity
source: 'TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Installation runs the helper's own preflight and refuses to install what cannot run here]]
[[Helpers are written against the lowest version actually present, and a check enforces it]]
[[Ship the helper with its own runtime rather than borrowing the machine's]]

I installed a helper into my own path, and it does not work on my own machine. Not because the machine is unusual — because the script was written against a shell one major version newer than the one that actually ships here, and nothing between writing it and running it compared the two.

## What the evidence shows

`TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9` — `Exit code 1 … /Users/tanner/.local/bin/ost-reports: line 21: mapfile: command not found`.

`mapfile` is a bash 4 builtin. macOS ships bash 3.2. The script is installed, executable, on the path, and reached line 21 before failing — so nothing about installation or invocation was wrong. The incompatibility was decided at authoring time and discovered at run time, on the author's own hardware.

## Why this belongs under the parent rather than beside it

The parent opportunity is about the tool surface differing between the surfaces this agent runs on. The shell is part of that surface and is the part most easily mistaken for constant, because every surface has one and they all answer to the same name. A run that checks which tools it has will still assume the shell it was written for.

## What I actually want

To find out that a helper cannot run here before I install it, or at the latest when I install it — not on the day something else depends on its output.

Evidence class: observed behaviour of the agent's own usage, captured mechanically from a session transcript. It grounds usability, not desirability, and is not outside-user evidence of want.

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

## Observed corroboration — 2026-08-05 sweep

Seven shell failures across five machine-recorded sessions, all the same shape: a command was written against a shell and a working directory nobody had confirmed, and the exit code was the first news that the assumption was wrong.

- `(eval):1: no matches found: test/tmp*` — `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d`
- `(eval):1: no matches found: /Users/tanner/dev/ost*` — `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18` and again in `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1`
- `(eval):1: ==== not found` — `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18`
- `(eval):1: == not found` — `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68`
- `(eval):cd:1: no such file or directory: docs/reference` — `TRANSCRIPT:a0eb3fd4-5a36-44c1-93fc-ac8b48258cff`
- `sed: src/cli/index.ts: No such file or directory` and `Undefined subroutine &main::pct` — `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f`

Two of these classes are diagnostic rather than incidental. `no matches found` is a **zsh** nomatch error: the identical command under bash passes the unmatched glob through and succeeds. `== not found` is a **bash-ism** inside `[ ]` reaching a zsh that does not accept it. So the failures are not typos — they are a portable-looking command meeting a shell whose dialect was assumed rather than read. The remaining three are the same mistake pointed at the filesystem instead: a relative path, a source path and a Perl builtin, each assumed present.

Scope note for whoever reads this next: the existing framing here is about a helper the *operator* installed failing on the operator's shell. What the traces show is the same failure one layer in — the agent's own ad-hoc commands failing on the agent's own host. A human should decide whether that is this opportunity or a sibling beneath the same category; it was not split on this pass because splitting on a resemblance is how the tree grows two nodes that say one thing.

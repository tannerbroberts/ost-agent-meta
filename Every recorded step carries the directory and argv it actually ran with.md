---
type: Solution
created: '2026-07-27'
evidence: observed
---
#Solution #evidence/observed

**The idea.** `loop step` records `cwd` and the resolved argv next to the exit code it already stores, so a recorded failure can be re-run verbatim from the record.

**What produced it.** Observed twice in one pass (2026-07-27): the same command recorded exit 1 and exit 0 in the same run, differing only in the directory it was invoked from, with nothing in the record naming that difference. The health file is deterministic, append-only, and — for those two entries — not diagnostic.

**Why it is worth more than it looks.** The whole health-bookend design rests on a claim that the record is the thing you can trust when nobody was watching. A number that cannot be reproduced from its own record weakens that claim in exactly the place the design is load-bearing. This is one field.

**Where it fails.** `cwd` is necessary and not sufficient — environment variables, the node/pnpm version, and the state of `node_modules` all move the exit code too, and recording all of them turns a health record into a container image. There is a real judgement about where to stop, and this node does not answer it; it argues only that the directory is on the necessary side of any reasonable line.

⚠️ Unvalidated. Agent-ideated from an observed failure in this pass's own health record.

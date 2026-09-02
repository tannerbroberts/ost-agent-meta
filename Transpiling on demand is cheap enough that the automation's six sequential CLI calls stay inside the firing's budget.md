---
type: Assumption
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

The belief, stated so it could be false: a runtime TypeScript loader starts fast enough that removing the bundle costs no meaningful wall-clock at the rate this product actually invokes its own CLI.

**Why this is the load-bearing one for that candidate.** Removing the artefact is unarguably correct on the axis it was ideated for — a thing that is not there cannot be stale. The only real question is what it costs, and the cost lands entirely on startup, paid per invocation.

**Why it is in doubt, with the multiplier named.** `examples/automation/build-pass.sh` invokes the CLI six times in one script — `build-check`, `gate`, `buildable`, `verify`, `check`, `debt` — read first-party this pass. So whatever a cold start costs is paid six times per build pass, and again on every firing. A bundle is a single file the runtime parses once; a loader walks and transpiles the module graph. Those are different orders of work, and the sibling candidates exist precisely because this one might lose on it.

**What would make it false.** A cold start materially slower than the bundled entrypoint, multiplied by six. The candidate's own kill criterion sets that threshold at more than double on the same machine.

Unvalidated. Agent-surfaced 2026-09-02; a human to review.

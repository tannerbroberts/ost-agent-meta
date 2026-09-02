---
type: Solution
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
killIf: >-
  A firing's cold-start time from invocation to first CLI answer more than
  doubles against the bundled entrypoint on the same machine
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: who-does-the-work. Position taken: nobody — the step is removed rather than assigned.**

Stop shipping a run path that has two representations of the same code. Invoke the TypeScript sources directly through a runtime loader, so `src/loop/handoff.ts` is what actually executes and `src/loop/handoff.js` is a path nothing ever reaches for. There is then no artefact to be stale, no moment at which source and build disagree, and no step that a person, an agent or a script can fail to run — because the step does not exist.

**Why this position and not another.** The two siblings both keep the compile and argue about who is responsible for it: one automates the detection of its absence, one hands the responsibility to the package manager. This candidate says the failure is not a missed step but a redundant representation, and that the cheapest thing that cannot go stale is a thing that is not there. It is the only one of the three under which the observed error becomes unreachable rather than better reported.

**What it deliberately does not do.** It takes no view on distribution. A published package may still ship a bundle for consumers who should not need a TypeScript loader; this is about the *development and firing* path, where the source is present and is the thing being edited. Conflating the two is how this candidate would get argued down for the wrong reason.

**What it gives up, plainly, and it is a real cost.** Startup. A loader that transpiles on demand pays on every invocation, and this repository's automation invokes the CLI six times in one script (`examples/automation/build-pass.sh` runs `build-check`, `gate`, `buildable`, `verify`, `check` and `debt`) — so the cost is multiplied by exactly the pattern the product already uses. It also adds a runtime dependency to the hot path, which is a new class of thing that can break, and it makes the executed code differ from the code a consumer of the published bundle runs, so a bug that only appears after bundling would stop being caught by the firings.

**What would make this the wrong pick.** If the startup cost is material at the observed invocation rate, the staleness-refusal sibling is strictly better: it keeps the fast path and only makes the failure legible. If bundling ever introduces a behaviour difference that a firing needs to catch, this candidate hides it by construction.

**Honest note on how this was ideated.** The sweep marked this opportunity `ideation: "blind"` and assigned one dimension per candidate. This surface holds no grant to run independent parallel ideators, so all three candidates here were composed in one context by one author — the exact condition the blind rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-02; a human to review.

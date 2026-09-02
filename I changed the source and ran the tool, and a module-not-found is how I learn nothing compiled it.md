---
type: Opportunity
source: 'TRANSCRIPT:e6056286-1e53-4585-8205-9d8be5c215dd'
created: '2026-09-02'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Take the compiled artefact off the run path entirely, so there is no build step to forget]]
[[The entrypoint refuses when its artefact is older than the sources it was built from, and names the rebuild]]
[[Adopt the package manager's own lifecycle hooks so the rebuild is a convention rather than machinery built here]]

**The need.** A firing edits source, then invokes the tool it just edited, and the first thing it learns is `Cannot find module './src/loop/handoff.js'`. The module is not missing — `src/loop/handoff.ts` is right there. What is missing is any step between writing the source and running it that turns one into the other. With nobody watching, the crash is the notification, and it arrives at the point where the firing had already committed to the run.

**Why this is stated as a need and not as "add a build step".** Adding a build step is one way to meet it, and the litmus test below shows it is not the only one, which is what keeps this on the opportunity layer.

**Litmus test (more than one way to address?):** Yes, and they differ in kind rather than in detail — compile before invoking, as part of the invocation; resolve TypeScript directly at run time so no compiled artefact is on the path at all; have the entrypoint detect that the artefact is older than the sources it was built from and refuse with a sentence naming the command to run, rather than failing at module resolution; or order the loop's own steps so that nothing invokes the CLI in a firing that has touched its source. Passes.

**Provenance: two independent sessions, one signature class.**

- This firing's own ingest, `TRANSCRIPT:e6056286-1e53-4585-8205-9d8be5c215dd` (mirrored 0d ago): `tool_error` (Bash), `Exit code 1 … Error: Cannot find module './src/loop/handoff.js'`, in a session whose own report records that it had just built the pass handoff record and `ost-agent loop handoff`. So the session wrote `src/loop/handoff.ts` and then ran something that expected `src/loop/handoff.js`.
- The 2026-08-31 signature census recorded on "A human-edited manifest of loop-prescribed call sequences the harvester suppresses" listed `Cannot find module './src/security/tools.js'` among four singletons it could not trace to any node. Same shape, different module, different session.

That census stated plainly that it made no claim the singletons were unmapped, only that it had not found a node for them. This pass found no node either, and now has a second instance, so the class is recorded here rather than left to be re-encountered a third time.

**What the repository says, read first-party this pass.** `src/loop/` holds 39 `.ts` files including `handoff.ts`; there is no `.js` beside them. `examples/automation/build-pass.sh` invokes `node "$OST_AGENT_DIR/dist/ost-agent.mjs"` — so the committed automation's supported path is the bundle, not a source path. The failing invocation reached for `./src/…​.js`, which is neither the source that exists nor the bundle the automation uses: it is a third path that is correct in neither layout.

**What this does not establish.** Two occurrences are not a rate, and this pass did not measure how many of the 578 unmapped records carry this signature — the prior census found it once in 26 events across 7 records, which is the only figure anyone has. It also does not establish which of the four framings above is right; that is solution-space and belongs beneath this node, not in it. And the evidence is this product's own agent using this product: it grounds usability and feasibility, and is not evidence that anyone outside the building wants anything.

**For a human to review:** whether this is genuinely distinct from the failure-attribution branch under "A test that failed because the machine was busy looks exactly like one that failed because I broke something". The judgement taken here is that it is: that branch is about failures whose *cause* is ambiguous, and this one's cause is perfectly legible — the defect is that the firing had no way to know before it ran, not that it could not tell afterwards. If a reader disagrees, these merge.

Unvalidated — mapped by an unattended sweep on 2026-09-02, no solutions ideated here deliberately, so the next sweep can ideate them under the blind-ideation rule rather than having them composed in one breath by the pass that wrote the need.

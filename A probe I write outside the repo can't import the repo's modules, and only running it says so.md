---
type: Opportunity
source: 'TRANSCRIPT:0555db5d-cab6-4293-868f-48c1ef8eb1fa'
created: '2026-08-21'
evidence: observed
---
#Opportunity #build-loop #transcript-friction #unvalidated #evidence/observed
[[A gitignored scratch directory inside the checkout, named in the build prompt, so a probe resolves like any repo file]]

**The need (the build agent's voice):** "When I want to poke one module of the product — call a function, print what it returns — I write a ten-line script somewhere scratch, run it, and it dies on the import before it reaches my question. The turn is spent learning where Node resolves packages from, not learning what the module does."

**What was observed (two sessions, both unattended build firings).** `TRANSCRIPT:0555db5d-cab6-4293-868f-48c1ef8eb1fa` (2026-08-20): `Exit code 1 … Error [ERR_MODULE_NOT_FOUND]: Cannot find package '@modelcontextprotocol/sdk' imported from /private/tmp/debug1.mts` — a scratch file in `/private/tmp` importing a dependency that only exists under the repo's `node_modules`. `TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11` (2026-08-17): `Error [ERR_MODULE_NOT_FOUND]: Cannot find module '/private/tmp/scripts/provenance-census.ts' imported from /private/tmp/census-smoke.mjs`, preceded in the same session by `Cannot find module './scripts/provenance-census.js'` — a scratch smoke script resolving a repo-relative path against `/tmp` instead of the checkout. Same shape both times: the probe lives outside the repo, Node resolves relative to the probe, the import fails, and nothing said so until the run.

**Why it is a need and not a typo.** Both sessions wrote the scratch file to the one directory a sandboxed session can always write, and both paid a turn for it. Nothing in the repo names a place a probe may live, a command that runs one with the repo's resolution, or a rule that says "don't." The agent is left to discover the resolution boundary by crossing it, once per firing that wants a probe.

**Distinct from its neighbours.** "The session tries to write a file before it has read it this run…" is an ordering guard on a file that exists; this is a resolution failure on a file the session just created. "A test that failed because the machine was busy…" is a red that carries no information about cause; here the cause is fully stated in the error — the need is to not have to hit it. "A run's own leftovers break the next run's setup…" is state carried between firings; a `/tmp` probe leaves nothing behind and fails within its own firing.

**Litmus test (more than one way?):** a gitignored scratch directory inside the checkout so resolution is the repo's; a documented one-liner (`npx tsx -e` / `node --import`) that runs an inline probe with the repo's loader; a REPL or `eval` subcommand on the CLI that loads a named module; an instruction in the build prompt that probes go through the existing test runner as a throwaway spec. Distinct mechanisms with real trade-offs. Passes.

**Evidence rung and what it grounds.** `observed` — machine-captured from the agent's own transcripts, no narrator. Grounds usability of the build surface, not demand: no operator has said the lost turn matters to them, and two sessions is the minimum that separates a pattern from a one-off. Unvalidated; for human review.

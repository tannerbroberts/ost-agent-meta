---
type: Assumption
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Every automation entrypoint that runs the built bundle builds it first, and the check counts what it read]]

Feasibility belief, and this pass's repo read suggests it is currently FALSE — which is why it is worth stating as its own node rather than leaving inside another node's prose.

If dist is committed only on per-firing branches, the shared trunk carries a stale or absent bundle between firings. That is harmless only if every consumer builds what it runs. Two do not, both read in full this pass:

- `examples/automation/build-pass.sh` sets `CLI="$OST_AGENT_DIR/dist/ost-agent.mjs"` and calls `node "$CLI"` for `build-check`, `gate`, `buildable`, `verify`, `check` and `debt`, on every firing. No build step appears anywhere before the first invocation.
- `examples/automation/github-workflow.yml` points its MCP config at `node "$SRC/dist/ost-agent.mjs"` on a fresh runner that never installs or builds this project.

Stated so it could be false: every entrypoint that runs the built bundle either builds it first or declares that a stale bundle is acceptable for its purpose.

**Why this is the assumption to build against, rather than the one to abandon the candidate over.** The gap is not fatal — it is the work. This candidate is only viable if the consumers stop depending on trunk dist, so making that true is part of building it, and a spec that holds the entrypoints to it is a definition of done a builder can act on. The failure mode it prevents is specific and quiet: `build-pass.sh` runs `build-check` *through* the very bundle whose staleness it would be reporting on, so a trunk carrying an old dist produces a firing that checks the wrong code and says nothing is wrong.

Note this is a different claim from its sibling "Nothing downstream needs dist present and current on the shared trunk between firings". That one asks what consumers *need*; this asks what they currently *do*. The first is the operator's to answer, the second is the repository's — and conflating them is why the sibling's ask has sat unanswered.

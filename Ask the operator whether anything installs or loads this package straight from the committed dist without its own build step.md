---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Zero consumers found expecting a pre-built dist/ with no build step, or at
  least one named consumer
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: the operator confirms whether any installer, plugin loader, or downstream script currently expects dist/ to already exist in a fresh checkout with no build step. Threshold: none found, or at least one named.

A person outside the building is the measurement here: Which systems install or load this package, and how, is knowledge about deployment/distribution that only the operator (or whoever set those consumers up) has.

## Issues
- 2026-08-21 2026-08-21 (unattended sweep) — the repository names one such consumer, in committed code. `examples/automation/build-pass.sh` sets `CLI="$OST_AGENT_DIR/dist/ost-agent.mjs"` and invokes `node "$CLI"` for six CLI calls on every firing (`build-check`, `gate`, `buildable`, `verify`, `check`, `debt`). It contains no `npm ci`, no `npm install` and no `npm run bundle` — it loads the committed bundle straight, with no build step of its own. So this question's "does anything load the committed dist without building it" half is answered yes without asking anybody, and what remains for the operator is the deployment half: whether any OTHER consumer (an install path, a plugin host, a second machine) does the same. Recorded in more detail on the sibling test "Ask the operator whether anything reads dist directly off the shared trunk between firings", which this pass annotated with the same read; the two questions overlap and a human answering one should read both. NOT ACTING: the lane is humans-required and this surface does not remove a caution. To re-lane: ost-agent lane "Ask the operator whether anything installs or loads this package straight from the committed dist without its own build step" --set compute-only. Source: this pass's `ost_read_repo` read of examples/automation/build-pass.sh. First-party read of committed code; grounds feasibility only. No command executed, no result recorded, rung unchanged.

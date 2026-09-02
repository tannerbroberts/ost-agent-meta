---
type: Solution
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
killIf: >-
  A hook is observed being bypassed on the automation's real invocation path, so
  the rebuild does not run in the place the failure was actually seen
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The invocations that actually crash go through the package manager, so a lifecycle hook is on their path]]

**Variation dimension: bought-vs-built. Position taken: the triggering is adopted from outside as it is; nothing here is built except the script the hook already calls.**

Write no detector and no refusal. Use the lifecycle hooks npm already runs — `prepare` on install, and a `pre`-prefixed hook on whatever script the firing actually enters through — so the rebuild happens at the moments the package manager already defines as "before this runs". The mechanism is documented, understood by anyone who has used Node, maintained by someone else, and already on the path for install and for `npm run`.

**Why buy rather than build.** Both siblings add a thing to this repository that has to be correct and stay correct: a runtime loader on the hot path, or a staleness predicate over mtimes with its own false-positive behaviour. Neither is hard, and both are a small permanent liability for a problem that a twenty-year-old convention already has an answer to. If the hooks cover the real invocation path, the other two are bespoke solutions to a solved problem, and finding that out is cheap.

**Why this position and not another.** The staleness sibling reports; the removal sibling eliminates; this one delegates. Its distinguishing bet is that the invocations that matter go through the package manager, which is exactly the bet the observed evidence puts under strain — see below.

**What it gives up, and this is the sharpest objection to it.** Hooks only fire when the package manager is doing the invoking. The failure this branch was mapped from was a bare `node` call, and this repository's committed automation is bare `node` calls: `examples/automation/build-pass.sh` invokes `node "$OST_AGENT_DIR/dist/ost-agent.mjs"` directly, with no `npm ci` and no `npm run bundle` anywhere in it — read first-party this pass. So on today's automation this candidate would not have fired at the moment the crash happened. That does not sink it, because the automation is editable and routing those calls through an npm script is itself cheaper than either sibling; but it means this candidate is only correct in combination with a change to how the firings invoke the CLI, and that dependency should be stated when it is compared rather than discovered afterwards.

**What it also does not do.** It gives no signal at all when it does not fire. A bypassed hook is silent, so the failure mode of this candidate is precisely the failure mode it was meant to fix — you find out from the crash. The staleness sibling is strictly better on that one axis by construction.

**What would make this the wrong pick.** If the set of entrypoints is open-ended — anything anyone might type — hooks cannot cover it and one of the other two is needed. If the entrypoints are few and already scripted, this is the least code and the least maintenance of the three by a wide margin.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface has no grant to run the independent parallel ideators the sweep's `ideation: "blind"` marking asks for. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-02; a human to review.

## Definition of done

"Every CLI invocation in the committed automation reaches the binary through a lifecycle-hooked script, not a bare node call"

```
npx vitest run test/automation/cli-invocations-are-hooked.test.ts
```

The bar: zero bare `node .../ost-agent.mjs` invocations remain across every file in `examples/automation/`, and at least one lifecycle hook is asserted present in `package.json`. It is red today because `build-pass.sh` carries six such invocations and no `npm ci` or `npm run bundle` — the exact condition this candidate's stated give-up is about.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

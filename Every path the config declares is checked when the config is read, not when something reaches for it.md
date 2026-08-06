---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A config check can name a sense that is required and absent, not only validate the paths that are present]]

**The idea.** Config load validates every declared path: it must exist and be readable. A missing or unreadable one is a startup error naming the key and the offending value, printed once, before any work begins.

**Why here.** The gap is a *configuration* fact, and configuration facts are cheap to check exactly once at the moment the file is parsed. Discovering it mid-pass is strictly worse for the same information, and the operator who could fix it in ten seconds at setup is not present at the moment it surfaces.

**The case this vault actually presents, which shapes the design.** `product.repos` is absent while `adapters.transcript.projectDir` correctly names the same product directory. So a pure existence check is not enough to catch it — an absent key has no path to validate. The check has to include *required-but-absent*, which means the config needs a notion of which senses a vault intends to use. The cheapest honest version: if any key names a filesystem path, validate it; and if `product.repos` is absent while some other key names a repository, say so and suggest the value.

**Where it fails.** It cannot see the second half of what closed repo sight here. The `Glob` fallback was denied by the harness grant, not by config, and no amount of config validation reports on what tools the run will be given. A vault could pass this check cleanly and still be blind. It also turns a soft degradation into a hard stop, which is the right trade only if the operator is reachable — on an unattended hourly loop, refusing to start is a night of no discovery, and that may be worse than a degraded pass that says so.

**Compared with its siblings.** "A pass reports which of its senses were live" never blocks and never fixes — it makes the degradation visible and leaves the choice. "The step that needs the product repo declares it required" is the narrow version, gating one activity rather than the run. This is the earliest and bluntest of the three, and it is the only one that catches the problem before any compute is spent.

⚠️ Unvalidated. Agent-ideated from the agent's own blocked pass.

## Definition of done

"Load this vault's own config and require the check to name product.repos as absent"

```
npx vitest run test/config/declared-path-validation.test.ts
```

Green means config load emits exactly one diagnostic for a config shaped like this vault's — a repository named under `adapters.transcript.projectDir` with `product.repos` absent — naming the missing key and suggesting the value, and stays silent for a fully-configured vault and for one configuring neither. The two silent cases are load-bearing: without them this is a check that nags every correctly-configured vault.

It does not cover the harness-grant half. `Glob` on the product directory was denied on 2026-08-06 by permission, not by configuration, and no config check can see that.

---
type: Solution
source: 'agent:ideation-2026-08-02'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The registry is a path improvements actually travel down, promptly]]

**Candidate (unvalidated, agent-ideated — one of three deliberately different mechanisms under this opportunity).**

**The mechanism.** Before a pass does any work it resolves the newest published version of the agent from the registry, compares it to the version it is actually running, and either upgrades in place or halts with the delta named. The distinguishing commitment is the second half: a stale instance is not allowed to run a *quiet* pass. Today `npx -y ost-agent@latest mcp` already resolves latest by accident of the install path; nothing anywhere reports which version was resolved, so an instance running months-old tools looks identical in its output to one running HEAD.

**What it is good at.** It is the cheapest mechanism to build — the resolution step already exists inside `npx`, and the new part is a version line in the pass record plus a refusal. It needs no new channel, no new credential on the operator's side, and no change to how the vault is stored. It also closes the specific skew already recorded in this vault: a CLI upgrade that silently reopened 18 mapped evidence items would have been visible at the top of the pass rather than discovered later as a mystery in the counter.

**Where it fails, stated plainly, because this is the one a comparison should turn on.** It inherits the publish gap whole. This tree has recorded `npm whoami` returning `ENEEDAUTH` for five consecutive passes and again at four releases behind; during that stretch `@latest` resolved to 0.9.0 while v0.10.0 through v0.13.0 sat on `main`. A pull mechanism cannot propagate what was never published, so this candidate makes propagation depend on exactly the human-held credential the opportunity's parent branch is already blocked on. A halt-on-stale rule would also have converted that publish gap into a stopped loop — the mechanism's safety behaviour and its failure mode are the same behaviour.

**Compare against:** "The vault carries the agent it runs, upgraded by an ordinary git pull" removes the registry from the path entirely, and "A push channel the operator subscribes to, applied at the next safe checkpoint" moves the decision to the publisher's side. This one keeps the registry and keeps the operator passive.

**Assumption it rests on:** that the registry is a path improvements actually travel down in practice, not just in principle. Tested by "Replay the last ten releases and count how many a pull-at-start instance would have received".

## Definition of done

"Replay the last ten releases and count how many a pull-at-start instance would have received"

```
npx vitest run test/release/registry-propagation-lag.test.ts
```

Green means at least 8 of the last 10 versions cut on `main` were resolvable from the registry within 24 hours of their commit. It is red today because nothing computes propagation lag and no registry snapshot is committed to score against.

**This command can kill the solution rather than shape it, which is why it is the cheapest thing in this branch.** The assumption is not that an instance can resolve `@latest` — obviously it can — but that the registry is a path improvements actually travel down. This vault has already recorded the counter-evidence in passing, five passes running: `npm whoami` returning `ENEEDAUTH`, four releases cut and unpublished, `npx -y ost-agent@latest mcp` resolving to 0.9.0 while v0.10.0 through v0.13.0 sat on `main`. At 7 or fewer the candidate is killed rather than repaired, because the fix would be a publish credential and a release discipline — a different opportunity from this one.

**What green does NOT settle.** It measures this project's own release discipline over one publisher and a ten-release window, not the registry's reliability in general. It also says nothing about the second half of this solution — whether *refusing to run* is the right response to detected skew is a judgement about unattended operation that no propagation number reaches.

## History
- 2026-08-05 unlinked "Replay the last ten releases and count how many a pull-at-start instance would have received" — moved under "The registry is a path improvements actually travel down, promptly" — the belief this test measures now has a node of its own

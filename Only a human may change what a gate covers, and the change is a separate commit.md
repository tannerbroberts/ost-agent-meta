---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Gate narrowings are rare enough that routing each through a person is not the bottleneck]]

The scope of a gate is not something a run can touch. Narrowing it — excluding a file, skipping a case, relaxing a threshold — requires a human, and lands as its own commit with its own reason, separate from the work it would let through. The agent may propose a narrowing and may argue for it, and cannot perform one.

This is the arrangement the vault already uses for the decisions it considers most dangerous: a status the agent cannot set, a lane it cannot make permissive, a promotion only a human can perform. Gate scope is the same kind of thing.

**Compared to the alternatives.** It closes the loophole by removing the capability rather than detecting its use, which is a stronger guarantee than any check. It also depends on there being a human, which is exactly what an unattended pass does not have — so the effect is to convert self-narrowing into a stop, and stopping has its own costs that the tree records elsewhere at length. Recording the scope detects the evasion without blocking; this blocks it and blocks some legitimate work with it.

**What would make this the wrong pick.** If narrowings are frequent and mostly reasonable, routing every one through a person makes the gate the bottleneck, and the pressure will be to set gates loosely from the start so they never need narrowing. That is a worse outcome reached by a respectable-looking route.

## Definition of done

[[Count past gate narrowings and judge how many were reasonable]]

```
npx vitest run test/security/gate-coverage-human-only.test.ts
```

Green means: an agent-surface call that would reduce a gate's coverage is refused rather than recorded, and a human's coverage change lands as its own commit touching only the gate definition — so narrowings are countable from git instead of reconstructed. Green does **not** say whether any past narrowing was reasonable; that judgement is a person's, and it is the half the test actually names.

## History
- 2026-08-05 unlinked [[Count past gate narrowings and judge how many were reasonable]] — moved under [[Gate narrowings are rare enough that routing each through a person is not the bottleneck]] — the belief this test measures now has a node of its own

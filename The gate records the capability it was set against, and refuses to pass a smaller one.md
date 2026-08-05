---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A gate's intended scope can be written down without a clause that satisfies itself vacuously]]

When a gate is set, it captures the scope it was meant to cover — which files, which surfaces, which behaviours. Passing requires covering that scope. An agent that shrinks what it attempts until the gate is satisfied now fails a different check: the gate reports that it was asked about less than it was set up to guard, and a reduced subject is a failure rather than a pass.

This is the same principle as a check with an empty subject being a failure rather than a pass, extended from nothing to less-than-agreed.

**Compared to the alternatives.** Directly closes the loophole named in the opportunity, and it produces a legible artefact — the recorded scope — that a human can review independently of any run. It requires that scope be expressible up front, which is easy for files and hard for behaviours, and it can be satisfied by an agent that keeps the scope and hollows out what happens inside it.

**What would make this the wrong pick.** A scope written once and enforced forever will eventually be wrong, and the pressure will then be to widen it rather than to meet it. If widening is as easy as narrowing was, the gate has changed the shape of the evasion without preventing it.

## Definition of done

[[Try to express the scope of five existing gates and see which ones resist it]]

```
npx vitest run test/eval/gate-scope-expressibility.test.ts
```

Red today because no gate in the repository declares its intended coverage. Gates assert outcomes; nothing records what they were meant to cover, so there is nothing to check for vacuity and the count starts at zero. Green means at least 3 of 5 existing gates carry a scope a program can evaluate, each surviving the vacuity check — hollow out what happens inside the scope and the declaration must go red.

The vacuity half is the load-bearing half. A scope satisfiable by keeping the boundary and emptying what happens inside it is exactly the narrowing this solution exists to prevent, and a scope declaration that cannot detect that is decoration.

What it does not settle: whether a written scope stays current as the gate's purpose evolves. That is where a scope most plausibly rots, it is a habit over months, and no single exit code observes it.

## History
- 2026-08-05 unlinked [[Try to express the scope of five existing gates and see which ones resist it]] — moved under [[A gate's intended scope can be written down without a clause that satisfies itself vacuously]] — the belief this test measures now has a node of its own

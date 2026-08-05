---
type: Solution
status: unvalidated
source: 'ported:ost-agent-vault@57c3745 — agent-ideation'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Real prerequisite relationships exist between the tests already in the tree]]

**The idea.** Let one assumption test declare that another must be answered first, and let ordering fall out of the resulting graph rather than out of anyone's opinion. A strict OST is a tree; real discovery has cross-branch dependencies, and the tetrix instance demonstrated one spanning an entire top-level opportunity.

**The evidence that the schema is short a concept.** Given no way to express "this comes first," the tetrix agent invented tags — `#prerequisite`, `#unblocks-discovery`, `#feasibility`, `#agent-executable` — and then wrote the dependency out longhand in the test body, listing the four tests by name that could not be run until this one passed. Vocabulary invented under pressure, in the only field that accepts free text, is a schema gap announcing itself. Two instances, two vaults, and the same reach for structure that is not there.

**Why this beats ranking, where it applies.** Unblocking-leverage is a heuristic; a prerequisite edge is a claim that can be *wrong* and therefore checked. "You cannot run the community-seeding test until arrivals are measurable" is falsifiable — a human can look and say no, we could run it with a coarser proxy. Ranking scores are much harder to argue with, which sounds like a virtue and is not.

**The real cost, stated plainly.** This is the most invasive of the three solutions here. It changes the node schema, the link model (edges that are not parent-child), the read tools, and the hygiene rules — an OST validator that currently calls any non-hierarchical link an orphan or a dangling reference will need to learn the difference. It also introduces cycles as a new failure mode, and cycles among assumption tests are exactly the kind of thing an unattended agent could quietly create. Weigh that against the standing-briefing solution, which needs none of it.

**Order of operations.** If leverage ranking is built first, prerequisite edges are the natural way to feed it real data instead of prose inference. If the briefing is built first, this can wait indefinitely. Building this first would be building the most expensive option against the least evidence.

⚠️ Unvalidated. Proposed by an agent, from an agent's behaviour.

## History
- 2026-07-24 provenance repaired: frontmatter source was corrupted to ">-" by the 57c3745 vault merge; restored from the body's provenance footnote (human-authorized repair).
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Paper-map prerequisite pairs among the sixty existing tests]] — moved under [[Real prerequisite relationships exist between the tests already in the tree]] — the belief this test measures now has a node of its own

## Definition of done

[[Paper-map prerequisite pairs among the sixty existing tests]]

```
npx vitest run test/ost/test-prerequisite-edges.test.ts
```

Green means: the tree can hold what a paper map finds — a test can declare another as its prerequisite, cycles are refused, and the sweep reports a test whose prerequisite has no result as blocked instead of offering it. Green does **not** say which pairs are prerequisites; that reading is the human's map, and this only gives it somewhere to land. Worth noting the count in the test's title is now stale: sixty tests then, 272 now, so a map left on paper is wasted twice over.

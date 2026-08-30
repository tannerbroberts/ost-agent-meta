---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Schema patterns can reject everything the imperative checks reject, without widening what is accepted]]

**Variation dimension: bought-vs-built. Position taken: the aggregation is adopted from outside as it is; only the wording adapter is built here.**

The rules that currently serialise are mostly *shape* rules — a threshold needs a comparator next to a number, an instrument matches one anchored command form and carries no shell metacharacters. Shape rules are what JSON Schema exists to express. Move them out of the imperative checks and into the tools' own `inputSchema` as `pattern` constraints, then let a standard validator running in all-errors mode do the collecting. Ajv's `allErrors`, or Zod's issue array, are solved and battle-tested; nothing here has to invent an accumulator or maintain it.

Two things come free with that, which is the argument for buying rather than building. The constraints land in `inputSchema`, which is the object `tools/list` already ships to the caller — so the grammar stops being discoverable only by refusal and becomes part of what the caller is handed before it composes anything. And the objections arrive pre-aggregated, because collecting every violation is what these libraries do by default.

**What stays behind, and it is the honest limit.** Not every check is a shape rule. "This test is labelled humans-required" depends on the tree, not on the arguments, and no schema can express it — so it stays an imperative check that still throws, and a call that is both malformed and disqualified still costs two turns rather than one. This candidate fixes the majority class and leaves the cross-cutting checks exactly where they are.

**Against the siblings.** Unlike the accumulate-and-rank candidate, this needs no per-check rework and no hand-kept severity list — but it also cannot rank anything, and it leaves the tree-dependent checks untouched, which are precisely the disqualifying ones. Unlike the validate-only flag, it needs no caller discipline and improves the default path.

**What it gives up, plainly.** A dependency, in a codebase whose whole safety argument is about what it does and does not let happen — adding a validation library to the write path is adding third-party code between a caller and a vault write, and that deserves the scrutiny this product gives everything else on that path. The refusal wording degrades: a regex violation renders as "must match pattern /…/", where the current message explains what a threshold is for and why a restated sentence is refused, and rebuilding that expressiveness on top of a library's error objects is the work this candidate claims to avoid. A pattern is also strictly less expressive than the current checks, so the schema version may accept a threshold today's code rejects, which fails in the permissive direction.

**Cheapest form.** Add `pattern` to the `threshold` and `instrument` properties of the AssumptionTest-bearing tools, switch `validateToolInput` to a library in all-errors mode, and keep a lookup from property name to the existing hand-written explanation so the message quality survives.

**How it would be wrong.** If the current messages are doing more work than anyone credits — and their length suggests someone thought hard about them — then trading them for pattern violations makes refusals cheaper to produce and more expensive to act on, which is the opposite of what this opportunity asks for.

**Honest note on how this was ideated.** The sweep asks for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.

## Definition of done

"Every threshold and instrument the imperative checks reject today is still rejected by the schema patterns"

```
npx vitest run test/mcp/schema-pattern-parity.test.ts
```

The bar: exactly 0 inputs rejected by the imperative check become accepted by the pattern, across at least 12 cases. The spec does not exist yet, so the command files as `no-spec` rather than a genuine red — though of the three tests under this opportunity this is the one that comes closest to a strong red, because both predicates it compares are pure functions and half of the comparison already exists in `src/knowledge/instruments.ts`.

**Run this one first.** It is the only test of the three whose failure would retire its candidate outright: if the grammars cannot be expressed as patterns without widening what is accepted, this candidate is not merely more expensive than its siblings, it is unsafe, and the widening fails silently in the permissive direction.

**What this command does not settle:** message quality, which is this candidate's central trade. Parity of verdicts says nothing about parity of usefulness.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

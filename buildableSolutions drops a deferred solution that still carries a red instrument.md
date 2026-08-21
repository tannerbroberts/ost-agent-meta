---
type: AssumptionTest
source: 'agent-ideated:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  In a fixture vault holding 2 solutions that each carry a test observed red — 1
  `deferred`, 1 `unvalidated` — `buildableSolutions` returns exactly 1 entry,
  the unvalidated one. Today it returns 2. A run returning 2, or returning 1
  that is the wrong one, is a fail.
instrument: npx vitest run test/eval/buildable-status-filter.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

The assumption above says this is settleable by reading the loop's own source rather than by asking anyone. This pass read it, and the assumption is **confirmed in its second form — the filter is incomplete, not absent.** What follows is an observation of the code, not a recorded result; a result is a human's `ost-agent result` and nothing here clears a gate.

**What the source says (`src/eval/buildable.ts`, read in full this pass).** Two functions answer two different questions and only one of them consults status:

- `solutionsMissingInstruments` — the *discovery* queue — opens with `if (n.status === "deferred") continue;`, with a documented rationale: a deferred solution "says the opposite: this was abandoned, and there is no unbuilt behaviour left for a red instrument to define."
- `buildableSolutions` — what the *build* loop selects targets from — iterates every `Solution` and calls `permitFrom` with **no status check at all**. `permitFrom` does not check status either; it checks only that a test exists, declares an instrument, and has been observed red and not green.

So a `deferred` solution whose test still carries a red observation clears `buildPermit` and appears in `buildableSolutions`. That is precisely the hypothesised failure mode, and it is a real asymmetry: the same abandonment that removes a solution from discovery's queue leaves it in the builder's.

**This also rules out the alternative the parent solution named as its own disconfirmer.** The parent says the one-line predicate is the wrong fix "if the loop already filters on status and the real bug is that it's reading a stale snapshot." There is no snapshot — `buildableSolutions` takes `tree` as an argument and reads `n.status` off live nodes. Nothing caches. The predicate fix is the right shape.

**What the spec asserts.** `test/eval/buildable-status-filter.test.ts` builds a fixture vault (the pattern in `test/ost/next-work-status-filter.test.ts`, which already does this for `computeNextWork`) with two solutions, each carrying a test observed red — one `deferred`, one `unvalidated` — and asserts `buildableSolutions` returns only the unvalidated one.

**Why this is not covered already.** `test/ost/next-work-status-filter.test.ts` pins the deferred exclusion for `solutionsMissingInstruments`, through `computeNextWork`, and stops there. `test/ost/shipped-status-audit.test.ts` pins the `shipped` face. Nothing exercises `buildableSolutions` against status, which is why the gap survived.

**The kind of red this is, stated plainly.** The spec file does not exist, so the first observation files as `no-spec`, not `red`. That is not inert here: `confirmPermit` keeps a permit on a `no-spec` run when the test names a **bound** threshold, on the reasoning that a builder can build to a fixed bar where a missing file tells them nothing. The threshold above is bound (2 solutions in, exactly 1 out, today 2), so this hands over a definition of done. An agent cannot do better than this under the one instrument form the grammar admits — see the finding on "A pass that cannot see the repository cannot set an instrument at all".

**What a green here does NOT settle.** Only that the candidate pool stops including abandoned work. It says nothing about whether `deferred` is being applied correctly by whoever sets it, nor about the sibling failure mode where a target is chosen and *then* deferred mid-flight. It also cannot tell you whether excluding deferred solutions is what the operator wants — that is a judgement, and the ask already standing with them ("Ask someone with the build loop's target-selection source open whether it filters candidates on status") is now answerable from this node rather than from their memory.

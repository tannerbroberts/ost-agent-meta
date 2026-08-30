---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
threshold: >-
  at least 3 of 3 seeded defects named in one refusal, and exactly 0 files
  changed
instrument: npx vitest run test/mcp/validate-only-writes-nothing.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A temp vault, an in-memory transport and assertions about a response — every artifact is created by the spec itself.

**What the spec must assert, and the template is already in the repository.** `test/mcp/tool-input-validation.test.ts` is the model: it builds a temp vault with `initVault`, connects `createLazyOstMcpServer` over `InMemoryTransport.createLinkedPair()`, snapshots `fs.readdirSync(dir)` before the call, and asserts both the refusal text and that the directory is unchanged afterwards. Reuse that scaffold and assert:

1. An `ost_create_node` call for an AssumptionTest carrying `validate: true` and three seeded defects — a threshold with no comparator, an instrument carrying a `-t` filter, and a parent that does not exist — returns all three objections in one response.
2. `fs.readdirSync(dir)` is identical before and after, and the parent node's file is byte-identical, so no node, no commit and no ledger line was written.
3. The same call **without** `validate: true` returns the same set of objections, so the two paths cannot report different things — this is the assertion that matters, because a validate mode that checks less than the real call is worse than none.
4. A `validate: true` call that is entirely valid still writes nothing and says so, rather than succeeding quietly.

**Assertion 3 is the one worth insisting on.** A builder wiring a `validate` flag in front of `tool.run` gets 1, 2 and 4 nearly free; the divergence risk is that tree-dependent checks live inside the tool and get skipped by an early return, which is precisely the class of objection — the disqualifying ones — a caller most needs to hear.

**Why it fails today, stated honestly.** `test/mcp/validate-only-writes-nothing.test.ts` does not exist, so this run files as `no-spec` and mints no permit. That is the weaker of the two red forms and it is forced here rather than chosen: the behaviour is unbuilt, so any spec asserting it must live in a file nobody has written, and authoring a spec file is outside what this surface can do. What the instrument can still hand a builder is the assertion list above and the named template, so the work is writing four assertions rather than reconstructing the question.

**What a green would NOT settle, and it is the larger half.** That any caller ever spends a call on the flag. This test proves the mechanism is honest; the parent solution's sharpest risk is adoption, which no exit code reaches. A green here says nothing about desirability or viability, and a reader who treats it as evidence the candidate is worth building has over-read it.

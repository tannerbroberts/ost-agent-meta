---
type: AssumptionTest
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
threshold: >-
  zero retry events from the same-id fixture and exactly one from the two-id
  control
instrument: npx vitest run test/adapters/transcript-call-identity.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What the spec asserts.** Fixtures passed to `extractFriction`, every one using **distinct, explicit ids**. The existing `assistantTool` helper hard-codes `"t1"`, so the fixtures must not use it.
1. *Same id, two lines.* Two lines, both `"type":"assistant"` on purpose so the entry-type sibling cannot pass this by accident. Each holds a `tool_use` block with id `toolu_A`, name `mcp__ost-agent__ost_next_work`, input `{"evidence":"E"}`. Expect **no `retry` event**.
2. *Two ids, one signature (control).* The same name and input under ids `toolu_A` and `toolu_B`. Expect **exactly one `retry`**.
3. *Same-id error copy.* One `tool_use` with id `toolu_C`, then the same `tool_result` (`tool_use_id: "toolu_C"`, `is_error: true`) on two lines. Expect **exactly one `tool_error`**, so the error path is keyed on identity as well.

**Why it is red today, and how strongly.** The file does not exist yet, so today's run is `no-spec`: weak, and the same red any question would give. Once written, fixture 1 fails on its assertion against today's code, because the signature check ignores `id` and files a retry. Fixture 3 fails too, because every `is_error` block is pushed with no check on whether its `tool_use_id` was already reported. Fixture 2 passes today and is the control.

**Why fixture 1 uses two assistant lines.** It keeps this test honest against its sibling. Filtering by entry type would leave fixture 1 red, so passing it can only mean the id is being used. That keeps the two candidates' tests from collapsing into one.

**What it does not settle.** Whether the host ever reuses an id for two distinct calls. A green spec proves this code treats an id as identity. It does not prove the host keeps its side of that contract.

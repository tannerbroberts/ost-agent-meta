---
type: AssumptionTest
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
threshold: >-
  zero retry events from the blob fixture, exactly one from the two-turn
  control, and at least one tool_error from the error control
instrument: npx vitest run test/adapters/transcript-entry-types.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What the spec asserts.** Three fixtures, each passed to `extractFriction`:
1. *The blob copy.* One `"type":"assistant"` line holding a `tool_use` block with id `toolu_A`, name `mcp__ost-agent__ost_read_tree`, input `{"node":"X"}`. Then one `"type":"api-request-blob"` line whose `message.content` holds the same block, with the same id. Expect **no event whose `kind` is `retry`**. This is the shape observed in `TRANSCRIPT:8275c757-fcf0-46d1-9d35-bfab1fdd33f9`, lines 56 and 60.
2. *The real repeat, as a control.* Two `"type":"assistant"` lines with the same name and input but ids `toolu_A` and `toolu_B`. Expect **exactly one `retry`**. This proves the filter did not remove the retry class.
3. *The real error, as a control.* An assistant `tool_use` with id `toolu_C`, then a `"type":"user"` line whose `tool_result` has `tool_use_id: "toolu_C"` and `is_error: true`. Expect **at least one `tool_error`**.

**Why it is red today, and how strongly.** The file does not exist yet, so today's run is `no-spec`: weak, and the same red any question would give. Once written, fixture 1 fails on its assertion against today's `src/adapters/transcript.ts`, because `extractFriction` never reads `entry.type` and files a retry for the blob copy. Fixtures 2 and 3 pass today and must still pass after the change. They are controls, not the red.

**What it does not settle.** That the host never records a real turn only in a non-turn line. A green spec proves the code does what the candidate says, against fixtures this repository wrote. It does not prove the fixtures cover every line type the host writes.

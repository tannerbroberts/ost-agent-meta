---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  1 of 1 refusals for a digit-less threshold on a no-spec instrument contains
  the word threshold, and 0 of 1 name the spec path as the cause
instrument: npx vitest run test/security/create-node-refusal-names-field.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Feasibility test of one belief: that `ost_create_node`'s refusal can name the field that actually failed.

**What the spec does.** Builds the OST tools against a fixture vault with one configured product repo, calls `ost_create_node` for an AssumptionTest whose `instrument` names a spec file absent from that repo and whose `threshold` reads "at least five of twenty" (a fixed bar, no digits). Asserts the call is refused (today's behaviour, observed 2026-08-20), that the refusal text contains `threshold`, and that it does not present the instrument path as the cause. A second case supplies "at least 5 of 20" and asserts the write succeeds, pinning the rule the message is meant to explain.

**Why it is red today, and which kind of red.** The spec file does not exist — this is a **no-spec red**, declared as such: it fails for the same reason any question written on this path would fail, mints no permit, and is unfinished until a builder writes the spec and its `threshold`-naming assertion fails against today's message ("…cannot carry that instrument: `…`"). With the file written, the red becomes specific: today's text names the instrument and not the threshold. Named from the mechanism: the check lives in the `ost_create_node` body in `src/security/tools.ts`, not in the server's per-field `validateToolInput` path (read this pass).

**What it does not settle.** Whether a better-worded refusal changes what an unattended session does with it — a session that does not read past the first line is unhelped — and nothing about the sibling candidates, which remove or relocate the check rather than rewording it.

## Instrument Log
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/security/create-node-refusal-names-field.test.ts` — test/security/create-node-refusal-names-field.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/security/create-node-refusal-names-field.test.ts` — test/security/create-node-refusal-names-field.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/security/create-node-refusal-names-field.test.ts` — test/security/create-node-refusal-names-field.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/security/create-node-refusal-names-field.test.ts` — test/security/create-node-refusal-names-field.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/security/create-node-refusal-names-field.test.ts` — test/security/create-node-refusal-names-field.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/security/create-node-refusal-names-field.test.ts` — test/security/create-node-refusal-names-field.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/security/create-node-refusal-names-field.test.ts` — test/security/create-node-refusal-names-field.test.ts does not exist — no spec was collected, so nothing was measured

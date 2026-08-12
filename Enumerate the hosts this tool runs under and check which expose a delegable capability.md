---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 2 surfaces expose a delegable capability, covering the majority of
  actual runs.
instrument: npx vitest run test/security/host-credential-delegation.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the hosts this tool actually runs under expose a way to act on the operator's behalf. If they do not, the route is unavailable regardless of how attractive it is, and a cron job or bare shell gets nothing from it either way.

**Risk category: feasibility.**

**Design.** List the surfaces this tool runs on — agent session, editor extension, terminal CLI, scheduled job. For each, check the documentation for a way to have the host perform an authenticated action, and note the scope that would come with it. Weight by how often the tool actually runs there.

**Why it is small.** Documentation reading against a list of four or five surfaces.

**What it will not cover.** Capability is not scope. A host that will act on the operator's behalf may only do so as their whole signed-in self, which is a much larger grant than a narrow token — that question is separate and matters as much.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/security/host-credential-delegation.test.ts — The enumeration is bounded by this repository — the hosts it ships adapters and entry points for are committed, so the spec asserts that for each one the code either resolves a host-held credential or records that the host exposes none; it fails today because no host-credential path exists and every route still asks the operator directly.

## What a green run does not settle

The enumeration is bounded by what this repository ships, and that is both why it can be a spec and the limit of what it proves. A host nobody has written an entry point for is invisible to the count, so green means "of the hosts we support, here is the delegation story", never "here is what hosts in general expose".

It is also a snapshot. Host capabilities change on someone else's release schedule, and a spec that passes today records what was true when it was written. Nothing in the assertion notices when a host adds or withdraws a delegable capability, which is exactly the event that would make this solution newly viable or newly broken.

Most importantly it does not touch the question underneath the solution: whether an operator *wants* the run acting under a host-held credential rather than one they issued deliberately. A capability being technically delegable and being something anyone should delegate are different claims, and only the first is in scope here.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/security/host-credential-delegation.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **green** (exit 0) `npx vitest run test/security/host-credential-delegation.test.ts` — Duration  750ms (transform 37ms, setup 0ms, collect 49ms, tests 494ms, environment 0ms, prepare 45ms)

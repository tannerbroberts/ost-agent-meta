---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  In a fixture where twenty items past the age limit share a signature already
  mapped to an opportunity and one item past the age limit matches no existing
  node, the twenty are collapsed into the backlog line and the one is still
  listed individually.
instrument: npx vitest run test/evidence/age-out-preserves-novel.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Whether age alone is a safe criterion, or whether ageing has to be qualified by something. The fixture is built so that pure age fails it: all twenty-one items are equally old, and only the novel one must survive. Passing therefore requires the rule to consult something besides the clock — which, if true, means this candidate is not as judgement-free as its node claims, and that is the finding worth having.

**Why it is red today.** Nothing ages out; every unmapped item is listed on every pass regardless of how many passes have declined it.

**Honest limit on the instrument.** No repository sight was available, so the path is invented and fails first for absence. A builder should fold these assertions into the existing spec for the evidence store.

**What a green here does not settle.** Whether the operator notices the backlog line, and whether a quiet queue causes the tooling gap underneath it to stop being fixed — which is this candidate's stated failure mode and is about people, not code.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/evidence/age-out-preserves-novel.test.ts` — No test files found, exiting with code 1

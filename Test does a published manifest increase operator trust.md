---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/release/capability-manifest.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Desirability.** Riskiest assumption: security-conscious operators actually want an inspectable capability manifest + signed build, and it moves their willingness to run the tool unattended.

**Proposed test (small, fast):** Show the manifest and signature verification to ~5 security-minded operators; ask whether it changes their trust/adoption stance.

**Pre-committed success threshold:** ≥3 of 5 report a meaningful increase in willingness to run unattended.

_Proposal only — a human runs this with real operators. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/release/capability-manifest.test.ts — A manifest can only increase trust if it is checkable, and an unverifiable manifest is a claim rather than evidence — which would make the whole test measure a reader's credulity. This asserts the checkable half: the release publishes a manifest enumerating every capability the agent surface exposes, the manifest is signed and the signature verifies against the built artefact, and a build whose actual tool surface differs from its manifest fails the release rather than shipping. Missing-spec red, not assertion red — no manifest is published, so the command fails on a missing file; a builder should write it against the real release path so it goes red on a surface/manifest divergence. It does not settle whether operators TRUST it more, which is a person's reaction and stays with a human.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/release/capability-manifest.test.ts` — No test files found, exiting with code 1

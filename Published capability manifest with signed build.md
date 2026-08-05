---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-runtime-decision.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test does a published manifest increase operator trust]]

**Candidate solution (unvalidated).** Publish the exact list of tools the agent can call as an inspectable manifest, and ship signed releases so an operator can verify the running binary matches the audited tool set. Proof is *inspectable*, not just asserted.

**Approach:** *verifiable transparency* about capability.

**Contrast with siblings:** the allowlist runner makes the claim true; this lets a skeptical operator confirm it without reading source; the red-team harness stress-tests it dynamically.

_Addresses: "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Definition of done

[[Test does a published manifest increase operator trust]]

```
npx vitest run test/release/capability-manifest.test.ts
```

Green means: the manifest is checkable rather than merely published — it enumerates every capability the agent surface exposes, its signature verifies against the built artefact, and a build whose real tool surface diverges from its manifest fails the release instead of shipping. An unverifiable manifest would make the test measure credulity rather than trust. Green does **not** mean operators trust it more; that is a person's reaction.

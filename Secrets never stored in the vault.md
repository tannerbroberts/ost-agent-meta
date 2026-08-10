---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[No secret ever lands in the vault or its history, and a scan can confirm it]]

**Candidate solution (unvalidated).** Credentials live only in the environment / OS keychain and are never written into the vault, so they can't leak into git history, a synced remote, or the tree itself. Blast radius of a compromised vault excludes the tokens.

**Approach:** *isolate the secret from the artifact*.

**Contrast with siblings:** read-only tokens limit what a leaked credential can do; this prevents the leak surface entirely; a local mirror removes live credentials from the run path altogether.

_Addresses: "Connecting my systems of record could leak or corrupt them". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test scan confirms no secret ever lands in vault or history" — moved under "No secret ever lands in the vault or its history, and a scan can confirm it" — the belief this test measures now has a node of its own

## Definition of done

"Test scan confirms no secret ever lands in vault or history"

```
npx vitest run test/security/no-secret-in-vault-or-history.test.ts
```

**One finding from the repository read that this node should absorb, because it complicates its own claim.** This solution says credentials "are never written into the vault, so they can't leak into git history, a synced remote, or the tree itself." Reading the code on 2026-08-09 shows the product deliberately writes a credential-derived artefact into the vault: `src/security/credential-audit.ts` puts the broker's audit log at `.ost-agent/credentials/audit.jsonl`, inside the vault, on purpose, and this product auto-commits every vault mutation. The header states the reasoning — the vault is what an operator already backs up and reads.

That is the audit property the broker exists to provide, so it is not a defect and this node should not be read as refuted. But the isolate-the-secret-from-the-artifact framing is now approximate rather than exact: what is isolated is the secret **value**, by `scrub()`, while the record of its use is committed by design. The claim this node can still make is narrower and worth stating in those terms — the vault carries the *use* of a credential, never the credential.

The command settles the narrow claim mechanically: seed a sentinel through the broker, run a pass, and assert the literal appears in no vault file and in no commit reachable from HEAD. It is red because no such scan exists anywhere in the repository, which the test node records in full along with two documented limits of `scrub` that a reading cannot close — it only knows secrets the broker holds, and it does not walk non-plain values.

**What it does not cover.** Whether an operator would trust a broker with a secret at all is a separate belief and a human study. And a green here proves nothing leaked on the paths the scan walks, not that the design is the right one.

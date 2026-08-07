---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility (potential-harm).** Riskiest assumption: the system can operate end-to-end while never writing credentials into the vault, and none leak into commits.

**Proposed test (small, fast):** Run a full ingest+maintenance pass with live tokens configured via env/keychain, then scan the vault contents and the entire git history for token/secret patterns.

**Pre-committed success threshold:** zero secret occurrences anywhere in the vault or its history.

_Proposal only — a human runs/reviews this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-07 2026-08-07 A mechanical test with no instrument, and the command is nearly writable — but this pass declined to set it, because it cannot tell whether the command would be red. Recorded here so the next pass with repository sight can set it in one call rather than re-deriving it.

This test needs no person. Its threshold is already an exit code: seed a sentinel credential through the configured-adapter path, run an ingest and maintenance pass, then assert the sentinel literal appears in no vault file and in no commit reachable from HEAD (`git log -p`). Roughly `npx vitest run test/security/no-secret-in-vault-or-history.test.ts`. It sits in `assumptionWork.needsHumans` only because it has no instrument, which overstates by one how much of this tree genuinely requires people.

Why it was not set anyway: the ruleset requires an instrument to be RED when written, and this one may be green on arrival. If the product already never writes credentials, the spec passes the day it lands, measures nothing, and gives a builder no definition of done — the exact failure the red-now rule exists to prevent. Deciding which it is needs a look at whether an adapter credential path exists at all; both configured adapters (atlassian, slack) are disabled in `ost.config.yaml`, so it is possible the end-to-end path this test describes has never been built, in which case the command is red for a good reason and should be set.

For whoever picks this up: check whether a credential ever reaches a write path. If it does and nothing scans, set the instrument above — it is red and load-bearing. If the path does not exist yet, set it anyway; it is red because the mechanism is absent, which is the right kind of red. If a scan already runs in CI, leave it and record that instead. This surface could not check: `product.repos` is unconfigured so `ost_read_repo` is unavailable, and direct reads of the product directory were denied.

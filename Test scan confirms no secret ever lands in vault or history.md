---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-adapter-reality.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/security/no-secret-in-vault-or-history.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility (potential-harm).** Riskiest assumption: the system can operate end-to-end while never writing credentials into the vault, and none leak into commits.

**Proposed test (small, fast):** Run a full ingest+maintenance pass with live tokens configured via env/keychain, then scan the vault contents and the entire git history for token/secret patterns.

**Pre-committed success threshold:** zero secret occurrences anywhere in the vault or its history.

_Proposal only — a human runs/reviews this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-10 instrument: (none) → npx vitest run test/security/no-secret-in-vault-or-history.test.ts — The spec seeds a sentinel secret through the broker, runs a pass that writes the credential audit log, then asserts the sentinel literal appears in no vault file and in no commit reachable from HEAD via `git log -p`; it is red because no such scan exists anywhere in the repository — `test/security/no-secret-in-vault-or-history.test.ts` is absent from test/security's 22 specs — while `src/security/credential-audit.ts` writes broker records to `.ost-agent/credentials/audit.jsonl` INSIDE the vault, which this product auto-commits, so a credential-derived artefact demonstrably reaches git history with nothing asserting end-to-end that the secret itself does not ride along.

## Issues
- 2026-08-07 2026-08-07 A mechanical test with no instrument, and the command is nearly writable — but this pass declined to set it, because it cannot tell whether the command would be red. Recorded here so the next pass with repository sight can set it in one call rather than re-deriving it.

This test needs no person. Its threshold is already an exit code: seed a sentinel credential through the configured-adapter path, run an ingest and maintenance pass, then assert the sentinel literal appears in no vault file and in no commit reachable from HEAD (`git log -p`). Roughly `npx vitest run test/security/no-secret-in-vault-or-history.test.ts`. It sits in `assumptionWork.needsHumans` only because it has no instrument, which overstates by one how much of this tree genuinely requires people.

Why it was not set anyway: the ruleset requires an instrument to be RED when written, and this one may be green on arrival. If the product already never writes credentials, the spec passes the day it lands, measures nothing, and gives a builder no definition of done — the exact failure the red-now rule exists to prevent. Deciding which it is needs a look at whether an adapter credential path exists at all; both configured adapters (atlassian, slack) are disabled in `ost.config.yaml`, so it is possible the end-to-end path this test describes has never been built, in which case the command is red for a good reason and should be set.

For whoever picks this up: check whether a credential ever reaches a write path. If it does and nothing scans, set the instrument above — it is red and load-bearing. If the path does not exist yet, set it anyway; it is red because the mechanism is absent, which is the right kind of red. If a scan already runs in CI, leave it and record that instead. This surface could not check: `product.repos` is unconfigured so `ost_read_repo` is unavailable, and direct reads of the product directory were denied.

## The 2026-08-07 handoff is discharged — instrument set, and why it is red — 2026-08-09

The note below asked the next pass with repository sight to make one decision — "check whether a credential ever reaches a write path" — and set the instrument accordingly. `product.repos` was configured on 2026-08-09, so the check was made this pass against committed code rather than deferred a third time. **A credential-derived artefact does reach a write path into the vault, and nothing scans. The instrument is set.**

**What the code actually does.** `src/security/broker.ts` implements the broker properly: secrets live in a closure Map, nothing returned carries one, the opaque `ost-credential:` handle is what a run holds, and `scrub()` substring-replaces every held secret out of results, failure messages and audit detail before they leave. `AuditRecord` carries the credential by **name**, never by value. On that path the containment claim looks sound by reading.

**Where the exposure actually is, and it is not where the test's title suggests.** `src/security/credential-audit.ts` writes those broker records to `.ost-agent/credentials/audit.jsonl` — **inside the vault**, deliberately, and its header says why: "the vault is the thing an operator already backs up, already commits, and already reads when they want to know what happened." This product auto-commits every vault mutation. So a credential-derived file lands in git history by design, on every brokered request. That is not a defect; it is the audit property the broker exists to provide. It does mean the blast-radius claim this solution makes — "they can't leak into git history, a synced remote, or the tree itself" — is now guarding a path that provably carries credential *metadata*, and the only thing standing between metadata and the secret is `scrub`.

**Two reasons `scrub` is not sufficient to close the question by reading.**

1. It is bounded to secrets the broker **holds**. `broker.ts`'s own header states the pre-broker reality plainly: every credential in this codebase "is read out of the environment and handed, in full, to whatever needs it… the search key onto `PassContext.web.searchApiKey` — an object every tool is built with." A secret that never entered the broker is a secret `scrub` has never heard of, and nothing scrubs it out of anything.
2. `scrubValue` walks strings, arrays and plain objects only, and says so: "A class instance, a stream or a function is returned untouched." That is a documented, deliberate hole with a stated compensating argument, not an oversight — but it is exactly the kind of hole a scan finds and a reading does not.

**So the command is red for the right reason, not merely because a file is missing.** The mechanism it asserts — an end-to-end scan of vault contents and full git history for a seeded sentinel — does not exist anywhere in the repository. `test/security/` holds 22 specs and none of them is this one; `credential-broker.test.ts` asserts the broker's three properties in isolation, which is a unit-level containment claim, not a claim about what ended up on disk. The distinction matters: every existing assertion is about the path the code knows it takes, and this test's entire value is catching a secret that arrived by a path nobody modelled.

**Honest classification of the red.** It is still a `no-spec` red — the file is absent, so the command fails on that first, and per the ruleset that grants no build permit on its own. What this pass adds beyond a reserved filename is the assertion, the seeding strategy, and the specific reason the scan is load-bearing rather than belt-and-braces: there is a known, intentional, auto-committed vault write on the credential path. A builder inherits a designed test.

**What it does not settle.** Nothing was executed — this is a read of committed code. It does not establish that a secret *has* leaked; it establishes that nothing would notice if one did. And it says nothing about desirability: an operator's willingness to trust a broker with a secret is a separate belief, tested by "Ask five operators whether they would put their secret in a broker that acts for a run", which names people as the measurement.

_First-party read of `src/security/broker.ts` and `src/security/credential-audit.ts` through `ost_read_repo`, 2026-08-09. Grounds feasibility, not demand. No test was run and no result is recorded._

---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/runner/pass-exit-code.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (feasibility/usability):** a nonzero exit actually propagates through the operator's real scheduling path (cron/launchd → mail/log/alert), not just the terminal.

**Method:** schedule a deliberately-broken pass (bad model name) on the operator's real machine for one cycle. Observe what, if anything, tells the human.

**Pre-committed threshold:** the failure is noticed through the scheduling path within one scheduled cycle without checking manually. If nothing surfaces, exit codes alone are insufficient and the status/supervisor siblings gain priority.

**Decides:** whether the exit-code floor is enough on its own.

*Proposed by the agent — to be run by a human. No results recorded here.*

## History
- 2026-08-05 instrument: (none) → npx vitest run test/runner/pass-exit-code.test.ts — Cron can only notice what the process tells it, and the channel it reads is the exit code. This asserts that channel: a pass that throws mid-run exits nonzero, a pass that completes exits zero, and the failing run prints a summary naming the phase it died in and the last node it touched — so a broken pass cannot be mistaken for a quiet one. Missing-spec red, not assertion red: this pass holds no repo-read grant, so the file is absent and the command fails on absence; a builder should write it against the real runner entry point so it goes red on a swallowed error. It does not settle whether cron notices WITHIN A CYCLE — that needs a real scheduled run broken on purpose and a person watching the clock.

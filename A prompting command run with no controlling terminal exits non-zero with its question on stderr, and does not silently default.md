---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At least 2 of 3 commands complete or exit non-zero with the question on
  stderr, and 0 of 3 exit 0 having changed nothing.
instrument: npx vitest run test/automation/no-tty-prompt-behaviour.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What this settles.** Whether the no-TTY launch produces a legible failure or the same silent default by another route. Take 3 commands drawn from the shapes an unattended firing actually runs — an interactive `cp` onto an existing file, a `git` operation that would prompt for credentials, an `rm` of a write-protected path — and run each twice against a temp fixture: once with a pseudo-terminal attached, once with stdin closed and no controlling terminal and `CI=1`, `GIT_TERMINAL_PROMPT=0`, `DEBIAN_FRONTEND=noninteractive` set. Compare exit code, stderr, and whether the filesystem changed.

**Pre-committed threshold:** in the no-TTY arm, at least 2 of the 3 commands either complete the work or exit non-zero with the question text on stderr, and 0 of the 3 both exit 0 and leave the filesystem unchanged. A command that blocks for more than 5 seconds counts as a failure of this test, not as a timeout of it — hanging is failure mode 2 in the assumption above, and it refutes.

**Why the spec fails today.** Nothing in `test/` launches a subprocess under a pseudo-terminal to compare the two arms; `test/automation/` and `test/preflight/` exercise script contents rather than TTY behaviour, and there is no pty helper in the suite to reuse. The named spec has to build the pty/no-pty harness, which does not exist.

**Stated so it is not over-read: this is a no-spec red.** The file below has not been written, so today it fails as any unwritten file does. It carries a bound bar, which is what makes it a working build permit rather than a vacuous one.

**What a green here does NOT settle.** Only that the failure becomes visible. It does not settle whether a loud refusal is an acceptable outcome for the operator — under this solution the overwrite in the founding evidence still does not happen, it just says so. That is the sibling policy-shim candidate's territory and a person's judgement. Desirability, viability and usability all untouched.

**Category:** feasibility.

---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: 'The known failure is flagged, with at most 2 false alarms across all helpers.'
instrument: npx vitest run test/runner/helper-bash-compat-lint.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a linter configured to a version floor catches this class. It reads what the script actually does rather than what someone declared, so it cannot be defeated by an undeclared dependency — but it protects only against version drift, and a missing command that exists at every version is invisible to it.

**Risk category: feasibility.**

**Design.** Configure an existing shell linter to a bash 3.2 floor and run it over every helper in the project. Check that it flags the known `mapfile` use. Then count total findings and have a person mark each as a real incompatibility or a false alarm.

**Why it is small.** The linter exists off the shelf, the helpers exist, and the run is seconds.

**What it will not cover.** A high false-alarm rate is what would actually kill this — a check people learn to ignore. That count matters more than whether the known failure is caught, which is nearly certain.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/helper-bash-compat-lint.test.ts — The threshold — the known failure is flagged, with at most 2 false alarms across all helpers — is machine-checkable against a committed expected-findings fixture: the spec runs the shell linter at a bash 3.2 floor over every helper the project installs, asserts the known `mapfile` use is among the findings, and asserts the count of findings outside the fixture is at most 2. It fails today because no linter is configured at a version floor and nothing runs over the helpers.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/helper-bash-compat-lint.test.ts` — No test files found, exiting with code 1
- 2026-08-22 **green** (exit 0) `npx vitest run test/runner/helper-bash-compat-lint.test.ts` — Duration  276ms (transform 29ms, setup 0ms, collect 55ms, tests 8ms, environment 0ms, prepare 34ms)

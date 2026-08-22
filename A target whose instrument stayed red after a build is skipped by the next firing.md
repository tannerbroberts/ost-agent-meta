---
type: AssumptionTest
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  Across 3 consecutive firings the target is selected exactly 1 time and skipped
  2 times.
instrument: npx vitest run test/loop/build-attempt-ledger.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What this settles.** Whether the loop remembers a failed build attempt across firings, without depending on the vault's `deferred` status being set by a human or a maintenance pass. Drive three consecutive simulated firings over a fixture vault in which the first build leaves the target's own instrument still red, and count how many times that target is selected.

**Pre-committed threshold:** across 3 consecutive firings the target is selected exactly 1 time and skipped 2 times. Selection on 2 or more firings means no memory exists and the assumption is supported; selection on exactly 1 refutes it, because a record already exists somewhere this pass did not read.

**Why the spec fails today.** Nothing in `src/loop/` holds a per-target attempt record. `src/loop/state.ts` names the health ledger and the firing lock as the only two files a firing must write to `.git/ost-agent/`, and the 28 modules beside it are lock, health, journal, spend, stall, scope, cadence, claim and replay — none of them target selection. `src/loop/corrections.ts`, the one cross-session ledger, records refused tool calls rather than failed build targets. The named spec has to construct the three-firing fixture and assert the skip, which is behaviour that does not exist.

**Stated so it is not over-read: this is a no-spec red.** The file below has not been written, so today it fails for the reason any unwritten file fails. It carries a bound bar, which is what makes it a working build permit rather than a vacuous one. A builder's whole job is to make the skip on firings 2 and 3 true.

**Why this exists beside the ask, rather than replacing it.** The sibling test asks a person to read the build loop's source. That source is in this repository, so the mechanical half should not cost anyone an afternoon — this test takes it. What the ask still carries and this does not: the driver is `examples/automation/build-pass.sh`, a shell script outside the module tree, and a record written there would not show up in any `src/loop/` read.

**What a green here does NOT settle.** Nothing about whether a loop-side ledger is the right fix. The solution's own body names the cost — a second place the same fact can go stale, duplicating state the tree is supposed to own — and that trade is a design call no exit code holds. Feasibility only; desirability, viability and usability untouched.

**Category:** feasibility.

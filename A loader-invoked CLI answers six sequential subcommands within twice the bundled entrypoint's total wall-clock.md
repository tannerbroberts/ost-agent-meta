---
type: AssumptionTest
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
threshold: >-
  Loader total across the 6 subcommands is no more than 2x the bundle's total on
  the same machine in the same run, and every one of the 6 returns identical
  output under both.
instrument: npx vitest run test/perf/loader-vs-bundle-cold-start.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Run the same six subcommands the committed automation runs — `build-check`, `gate`, `buildable`, `verify`, `check`, `debt` — twice over: once through the bundled entrypoint, once through the loader, in the same process invocation on the same machine, and compare totals.

**Why it is measured this way and not as a single cold start.** A one-shot startup number is the wrong unit: the candidate's cost is per invocation and the automation invokes six times, so the figure that decides the question is the total across the sequence. Measuring one call and multiplying by six would also miss any warm-cache effect the loader gets from the second call onward, which is a real effect and cuts in this candidate's favour.

**Both arms in the same run, deliberately.** A ratio measured across two runs on a loaded machine measures the machine, not the change — this tree already carries a whole branch on failures that look like breakage and are load. Running both arms in one invocation makes the comparison self-normalising, so a busy machine slows both and the ratio survives.

**Pre-committed bar, fixed before anything runs.** Loader total no more than 2x the bundle total, and all six subcommands producing identical output under both. The 2x matches the parent candidate's own kill criterion, so a run that fails this test is a run that retires the candidate rather than one that starts an argument about what the number meant. The output-identity half is not decoration: a loader that is fast because it is running different code has answered a different question.

**Instrument honesty, stated rather than hidden.** `test/perf/loader-vs-bundle-cold-start.test.ts` does not exist, so the first run is filed `no-spec` and grants no build permit. Grammar limit, not choice — `ost_set_instrument` takes only a bare `npx vitest run <path>.test.ts` and refuses a `-t` filter. `test/perf/` is an existing directory, so the builder inherits its conventions. And a caution worth writing down: a timing assertion is the classic flaky spec, so whoever builds it should prefer a generous ratio held stably over a tight one that fails on a busy machine — a spec that goes red for load is the exact defect this tree maps elsewhere.

**What a green here does not settle.** Only cost. It says nothing about whether a loader introduces behaviour differences that appear solely after bundling — a real risk this candidate's own prose names and no timing test can see — and nothing about desirability or viability. A fast loader is still a change nobody has asked for.

⚠️ Proposed only — the agent does not run tests or record results.

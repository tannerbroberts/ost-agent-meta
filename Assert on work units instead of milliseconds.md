---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Work count tracks elapsed time closely enough to catch the regressions a clock would]]

**The idea.** Stop asserting on elapsed time. Assert on the countable work the operation performs — files read, nodes parsed, passes over the tree — with a fixed ceiling. A regression that makes `ost_next_work` slow almost always makes it slow by doing more work, and the work count is deterministic on a given vault regardless of how busy the machine is.

**Why it addresses the need.** It removes the failure mode entirely rather than damping it. A count cannot flake under CPU contention because contention does not change how many files get read. The verdict becomes reproducible: the same vault gives the same number on a loaded sandbox and an idle laptop, which is what makes a red result worth acting on.

**How it differs from its siblings.** [[Budget against a same-run baseline instead of against the clock]] keeps measuring time and tries to cancel the noise; this one changes the subject. That is the strength and the weakness in one move.

**Where it fails, and it is the honest objection.** The operator's actual concern is time — a pass that takes forever costs compute and wall-clock, and nobody cares how many files it read. A work-unit ceiling can stay green while the operation gets genuinely, painfully slower for reasons that are not work count: a pathological regex, an accidental O(n²) over already-loaded nodes, a synchronous call that blocks. This solution is only sound if work count is a good proxy for time in this codebase, and nobody has checked that. It is also the most invasive of the three, requiring instrumentation the code does not currently expose.

**A cheaper hybrid worth noting rather than filing as a fourth sibling.** Assert the work count as the gate and record the elapsed time as advisory output. The gate stops flaking; the number a human actually cares about stays visible and can be watched for drift without being able to fail a build. If a human likes this candidate at all, this is probably the form to build.

**Cost.** Medium: instrumentation, then the assertion.

⚠️ Unvalidated. Agent-ideated, 2026-08-02.

## Test

[[Measure whether work count actually tracks elapsed time across vault sizes]]

`npx vitest run test/telemetry/work-units-vs-elapsed.test.ts`

Green when work units correlate with elapsed time across vault-size fixtures above a committed bound, and stay identical across repeated runs of the same fixture. The stability half is the one that makes a gate reproducible and holds independently of the correlation. Blind by design to a change that makes each unit slower.

## History
- 2026-08-05 unlinked [[Measure whether work count actually tracks elapsed time across vault sizes]] — moved under [[Work count tracks elapsed time closely enough to catch the regressions a clock would]] — the belief this test measures now has a node of its own

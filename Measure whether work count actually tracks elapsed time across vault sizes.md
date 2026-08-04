---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/telemetry/work-units-vs-elapsed.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Whether the proxy is a proxy.

**The assumption under test.** That countable work is a good stand-in for elapsed time in this codebase. The candidate's honest objection is that the operator cares about time and a work-unit ceiling can stay green while the operation gets genuinely slower — a pathological regex, an accidental quadratic over already-loaded nodes, a synchronous blocking call. None of those change how many files are read. If work count and time diverge, the gate is green precisely when it matters.

**The test (measure the correlation before building the gate).** Instrument `ost_next_work` to emit both elapsed time and a work count (files read, nodes parsed, passes over the node set). Run it across at least six vault sizes spanning the realistic range — an empty vault, a fresh one, this vault at 241 nodes, and synthetic vaults at roughly 500, 1000, and 2000 nodes — on an otherwise idle machine, five repetitions each. Plot time against work count.

**Pre-committed threshold.** Time must be **monotonic in work count across all six sizes**, and the ratio of time to work count must vary by **no more than 2× across the whole range**. Monotonic but wildly non-linear means the count orders things correctly and cannot set a meaningful ceiling; non-monotonic means the proxy is simply wrong.

**Then run the negative case, because the positive one is not sufficient.** Plant each of the three named divergence shapes — a slow regex, a quadratic over loaded nodes, a synchronous block — and confirm work count stays flat while time rises. It will. The number worth recording is **how much slower the operation gets while the gate stays green**, because that number is the exact cost of choosing this candidate over its siblings, and it should be written into the node whatever the verdict.

**Likely outcome, recorded in advance so the result can contradict it.** The hybrid named in the solution — work count as the gate, elapsed time recorded as advisory — is expected to survive this test even if the pure form does not. A result showing poor correlation should be read as evidence for the hybrid rather than against the branch.

**Who runs it.** A human, or an attended session with a build environment.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/work-units-vs-elapsed.test.ts — Both quantities are produced by the suite itself — run a pass over vault fixtures of increasing size, record work units and elapsed milliseconds for each, and assert the two correlate above a committed bound while work units stay stable across repeated runs of the same fixture; it fails today because no work-unit counter exists to compare against the clock.

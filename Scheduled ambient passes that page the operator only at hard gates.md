---
type: Solution
status: unvalidated
source: >-
  founder-directive:2026-07-24 — compute-only actionability, stated in session
  as first operator
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Two unattended weeks - count pages, grind, and money burned]]

**The idea.** Invert who initiates: cron-scheduled ambient Claude sessions run the full maintenance loop (ingest, map, ideate where ungated, run compute-only tests, refresh the docket) with no human trigger. The operator is contacted only on pages — a hard gate hit (identity, money, validation) or an invariant failure. Silence means it's working; the weekly digest is the only scheduled human touchpoint.

**Contrast with siblings:** consumes the other two (runs the triage lane, refreshes the docket). Heaviest dependency: requires the failed-pass-exits-0 defect fixed first — an unattended loop that cannot signal failure is the trust branch's nightmare made real.

**Trade-off:** unattended cadence spends tokens without a human watching the meter; needs the protected-budget idea and idle-down before it can be trusted to not grind.

## Gate cleared — 2026-07-25

This solution was explicitly blocked behind the exit-0 defect (recorded on [[I need the tree's output to be actionable by compute alone, because my hours don't exist]]): paging on failure is meaningless when failure is indistinguishable from quiet success. That defect is fixed in v0.5.0 — `ost-agent run` exits nonzero and names the failure, and `schedule` logs it to stderr.

**What the fix does and does not give this candidate.** It gives the *page-on-error* half a mechanical trigger any wrapper can read. It gives the *silence-means-working* half nothing: a cron that stops firing produces no exit code at all, and this candidate's entire promise is that silence is trustworthy. Until something consumes journals on a heartbeat ([[Supervisor heartbeat consumes run journals and alerts on error]]), silence still means "either healthy or dead" — which is the state this candidate claims to have solved.

So: unblocked, not ready. The honest sequence is heartbeat first, then unattended scheduling.

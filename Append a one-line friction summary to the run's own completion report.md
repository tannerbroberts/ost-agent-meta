---
type: Solution
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators actually read the run's completion report closely enough to notice an appended friction line]]
[[The run's completion report is produced in one place that can carry a friction count]]

Whatever channel already tells the operator a run finished (a commit message, a status file, a completion note) gets one more line: how many tool_error / retry events this run hit. No new surface, no new place to check — the friction count rides along with information the operator already reads.

**Compared to the alternatives.** Cheapest to ship: it is pure addition to an existing report, not a new mechanism. It is also the easiest to ignore — a number appended to a report the operator already skims is exactly as visible as everything else in that report, no more.

**What would make this the wrong pick.** If operators do not actually read the completion report (they read status only through a different surface), the line goes unseen. It also gives no signal across runs — five roughs sessions in a row would each report quietly and never sum to a pattern the operator notices.

## Definition of done

"One completion path carries the run's friction counts, and a clean run says so explicitly"

```
npx vitest run test/friction/completion-report-line.test.ts
```

Red today because no completion path emits a friction line and the spec is unwritten; green when one path does and the zero case renders. Written blind of an existing spec, so its first observation files as `no-spec` — the pre-committed bar above is what carries a builder.

**This command settles feasibility only.** The desirability question — whether the operator reads the completion report closely enough for the line to land — is "Ask the operator how often they actually read the run's completion report", and this candidate's own prose concedes the line may go unseen. A green here does not answer that.

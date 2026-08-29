---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.**

Stated so it could be false, because the solution's own prose argues it probably is: `timeout(1)` is GNU coreutils and is **not present on a stock macOS**, where it ships only as `gtimeout` via Homebrew. The machine this loop runs on is a Mac. `src/loop/wait.ts` argues at length that the shim must be plain POSIX `sh` with no external dependency, precisely because anything that can go missing "fails as 'command not found' three weeks later and reads exactly like the affordance never existing."

So the belief under test is not "124 is a good convention" — it plainly is — but that the convention can be *adopted as a tool* rather than hand-copied as a number. If the binary is unreachable, the candidate silently degrades into hard-coding 124 in the shim, which buys the semantics without buying the maintenance, and is a materially different solution that should be judged on its own rather than substituted for this one.

**What settles it:** whether the shim, rendered onto a host with no coreutils `timeout` on PATH, still exits 124 on expiry. That is mechanical and needs nobody's afternoon.

**What a green here does NOT settle:** nothing about whether an operator wants a distinct expiry status at all, or whether any caller would branch on it. Feasibility answered mechanically leaves desirability and usability exactly where they were.

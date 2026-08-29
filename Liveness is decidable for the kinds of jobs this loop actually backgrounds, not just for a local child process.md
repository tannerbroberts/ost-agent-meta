---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

Stated so it could be false: *for the jobs this loop actually waits on, a check exists that distinguishes "still running" from "gone" reliably enough to authorise more spend on the answer.*

**Why this is the belief that decides the candidate.** The whole value of the three-valued wait is the middle value. If *still running* can only be established for a local child process — and the loop's real waits are on detached processes, work in another checkout, or a suite whose parent shell has already exited — then the mechanism returns *gone* or *unknown* exactly when a caller most needs *still running*, and a wait that says "unknown" is the two-valued wait this candidate set out to replace.

**The failure direction that matters, and it is asymmetric.** A false *gone* costs a wasted restart and is self-correcting. A false *still running* is the expensive one: it tells the caller to keep waiting on work that has already died, converting a bounded 300s loss into an unbounded one. The candidate's own prose names this — "a wait that reports *still running* by a weak check is worse than one that stays silent, because it authorises further spend on a false positive" — and it is why the bar below is about the weak direction rather than about overall accuracy.

**Grounded in what the loop actually does.** The observed session was waiting on a vitest suite writing to `/tmp/suite-baseline.txt`. That is the ordinary case here, and it is already harder than the easy one: the suite is started in the background and the waiting turn is not its parent, so there is no child to reap and liveness has to come from something other than the process tree the waiter sits in.

**What it does not cover.** Nothing about the manual half of this candidate — whether a caller-declared ceiling is one operators would actually set rather than leave at a default. That is a separate belief and no test here touches it.

---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

Stated so it could be false: *the waits this loop actually issues are mostly on work started through a channel the harness tracks, so replacing the poll with a completion notification would cover most of them.*

**Why this decides whether the candidate is the answer or a distraction.** Deleting the wait only works where something else announces completion. If the loop's real waiting is on jobs it backgrounded itself in a shell, nothing announces anything, and this candidate covers a sliver while leaving the expensive remainder to its siblings. The candidate's own prose names this as the first thing to check; the assumption is written out here so it can be answered rather than re-noticed.

**The available evidence points the wrong way for this candidate, and that is worth stating up front.** The one observed session — nine expiries, `TRANSCRIPT:2a686fb9-1bf7-4f01-b2f9-b66c8aea20ef` — was waiting on a vitest suite writing to `/tmp/suite-baseline.txt`, which is a shell-backgrounded job and not harness-tracked. `src/loop/wait.ts` records three more waiting cases lifted verbatim from refused calls, and their intents are polling a CI check via `gh`, listing a task's output directory, and testing a git-status condition. On that reading the assumption looks likely false. But four cases is not a census, they were selected for a different question, and the corpus that could answer it properly exists.

**Why it is still worth asking rather than assuming refuted.** A `refuted` verdict is not a null result here: it retires this candidate cheaply and redirects the branch onto the liveness sibling, which is the more expensive one to build and would otherwise be sequenced second. Establishing that early is worth more than the test costs.

**What it does not cover.** Nothing about whether a completion notification, where it does apply, is actually better than a poll — only about how much of the waiting it could reach. And nothing about mid-flight progress visibility, which the candidate gives up regardless of how this comes out.

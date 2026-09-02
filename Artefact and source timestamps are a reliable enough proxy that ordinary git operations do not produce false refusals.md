---
type: Assumption
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A source newer than the artefact refuses and names the rebuild, while a branch switch that changes no content still runs]]

**Risk category: feasibility.**

The belief, stated so it could be false: comparing the artefact's mtime against the newest source mtime separates a genuinely stale build from a fresh one accurately enough to be worth blocking on.

**Why this is the load-bearing one for that candidate.** The candidate's value is that it converts a crash three frames deep into a first-line refusal naming the fix. Every false refusal converts the opposite way — a firing stopped for nothing, with a message it cannot act on because nothing was actually wrong. A checker that cries wolf is worse than the crash it replaced, because the crash at least always meant something.

**Why it is in doubt.** mtimes are not content. A fresh clone, a branch switch, a `git stash pop`, a `git checkout` of an unchanged file, or any tool that rewrites files identically will move a source's mtime past the artefact's without changing a byte of what it compiles to. This repository's own automation runs on a shared checkout across firings, which is exactly the environment where that churn happens.

**What would make it false in the other direction.** A build system that preserves mtimes, or a source edited and reverted, leaves an artefact that looks fresh and is not. That direction is the less dangerous of the two — it degrades to today's behaviour — but it means a green here is not a guarantee.

Unvalidated. Agent-surfaced 2026-09-02; a human to review.

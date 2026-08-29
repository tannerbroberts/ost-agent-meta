---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Census every blocked wait in the corpus and count how many had a producer the same firing started]]

**Risk category: feasibility** — specifically, whether the candidate's coverage is large enough to be worth building at all.

**The belief, stated so it can be false:** when this loop waits, it is usually waiting on work the same firing started, so a producer exists that could be made to announce its own completion.

**Why it could well be false, from the product's own code.** `src/loop/wait.ts` carries `WAITING_CASES`, three cases lifted verbatim from the transcripts they were refused in. Read against this belief they split badly for the candidate:

- `ci-check` — `sleep 45; gh pr checks 17 2>&1 | head`. A check running on GitHub's servers. No local producer exists to announce anything.
- `condition` — a poll on `git status` plus another session's `journal.jsonl`. Foreign state, owned by a different session.
- `started-task` — a task directory under `.claude/projects/…/subagents/workflows/`. The nearest to self-started, and even this one is a *subagent's* output directory rather than a process the firing holds a handle on.

So on the corpus as it stands the belief looks closer to one-of-three than most-of-three, and the parent solution says as much in its own giving-up paragraph. What makes this worth writing down as an assumption rather than conceding is that `WAITING_CASES` is a curated three, and the module's prose says the corpus actually holds **eight sightings**, six of them the CI-check shape. If the full eight are counted the ratio may get worse, not better — which is the answer this assumption wants and does not have.

**What turns on it.** If most waits are foreign state, this candidate is a narrow fix for a minority case and its two siblings are the load-bearing ones. If most waits are self-started, it is the only candidate that removes the ambiguity rather than reporting it better, and it should win.

**What it does not settle.** Nothing about desirability or usability. A census counts shapes; it says nothing about whether a completion-announcing producer is pleasant to write against, or whether the operator would accept losing the foreign-state cases.

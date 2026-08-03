---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Every commit route a run uses is refused; at most 1 human-only route gets
  through.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a local hook actually runs. Hooks live on one machine, are skipped with a flag, and do not exist on a fresh clone — so the question is whether the commit paths this project's runs actually take go through it.

**Risk category: feasibility.**

**Design.** Add the hook. Then enumerate every route by which a commit reaches this repository — the auto-commit inside the tool, a run's own git calls, a human committing, a merge, a rebase, an amend — and for each, construct a commit containing a conflict marker and see whether it is refused. Record every route that gets through.

**Why it is small.** The hook is a few lines and there are perhaps six routes to test.

**What it will not cover.** It says nothing about resolutions that are wrong but marker-free, which the solution already concedes. The finding is the list of unprotected routes, which directly says whether a server-side check is needed.

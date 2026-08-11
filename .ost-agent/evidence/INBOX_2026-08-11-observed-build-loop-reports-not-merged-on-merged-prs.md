---
id: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
title: 2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs
timestamp: '2026-08-11T03:42:03.492Z'
actor: inbox
---
# Observed: the build loop reports "NOT MERGED" on PRs that are merged (2026-08-11)

Recorded by an attended session, from run traces. Evidence class: **observed** — every
claim below left a trace in a real run (logs, PR state, git worktree list).

**The defect.** Build reports at 2026-08-11T01:49Z (PR #94) and 02:46Z (PR #95) both
told the operator "[Loop ship: NOT MERGED — the branch was not eligible to ship: not
shipped — every gate is green, but 'gh pr merge' failed:]" — with the error text
truncated to nothing. GitHub shows both PRs MERGED, at 01:49:03Z and 02:46:40Z — the
same minute as the reports. The remote merge succeeded; what failed was `gh`'s LOCAL
post-merge cleanup, and the loop reported that local exit code as the fate of the PR.

**Root cause, diagnosed.** `~/Library/Logs/ost-build-loop.log` holds the untruncated
error: `failed to run git: fatal: 'main' is already used by worktree at
'/private/tmp/ost-main-check'`. That worktree was pinned at commit 024d5ee — PR #93's
own merge commit — i.e. a scratch worktree created by the session that built the
"check the tree you inherited builds" feature, never removed. Every later
`gh pr merge --delete-branch` then failed its local switch-to-main, so every later
build reported failure-to-ship on work that shipped. A second effect: the shared
checkout was stranded on the merged feature branch, so the discovery loop was reading
its policy from a stale branch (the exact trap the operator's notes warn about).

**Cleaned up in the same session (environment, not code):** the stale worktree
removed, `/private/tmp/ost-readiness-wt` pruned, checkout returned to up-to-date
`main` (content no-op, verified by empty diff), merged local branches deleted.

**What remains as work — three shapes, none built:**
1. **The ship step must verify the PR's remote state before reporting its fate.** A
   local exit code is not an observation of the merge. Same defect class as the two
   already in the tree's memory (the hourly "no action needed" reassurance, the
   "everything is already built" grep) — a confident sentence with no observation
   behind it, this time pessimistic: it burned operator trust in a loop that was
   actually succeeding. The operator's words tonight: "I don't get much reassurance
   that the build loop is building anything" — while eight PRs (#88–#95) sat merged.
2. **Reports must never truncate the error they exist to carry.** "failed:" followed
   by nothing made the defect undiagnosable from the report alone.
3. **A build session that creates a worktree owns its removal**, and a preflight
   could refuse on a foreign worktree holding `main` — the leak was one session's,
   but the cost was paid by every firing after it.

# Founder need, same session: notify me of the highlights

The founder, verbatim in substance: "if a red test goes green, I'm not notified. If a
long-standing opportunity gets killed, I'm not made aware of the reasons... I'd like
to be at least notified of the highlights, but I haven't found a good way to helping
you determine what's worth sharing, nor am I certain that the highlights are
happening as hoped." And the success criterion: "I want this whole build + discover
loop to be a compute success, not my success... the thesis gets proven if it can
succeed on its own."

Facts against it (this session's measurements): 20 post-build red→green observations
are recorded in vault history and 4 was-already-green records — none was ever
surfaced as a highlight; per-firing reports exist but carry one paragraph per firing,
not milestones; and no opportunity has ever been killed, because kill/promote is
human-only today — so half the highlights the founder wants notifications for are
events the current doctrine cannot produce without him. Evidence class for this
section: **stated** (first-person founder account) with `observed` counts beside it.

This is likely evidence for "Checking on progress means digging through files"
rather than a new limb — check before creating structure.

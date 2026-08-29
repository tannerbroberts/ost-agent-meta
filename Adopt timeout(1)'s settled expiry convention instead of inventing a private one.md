---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The expiry convention can be bought on the machine the loop actually runs on]]

**Variation dimension: bought-vs-built. Position taken: the expiry semantics are adopted from outside, unchanged; only the polling loop is built here.**

This problem is old and already has a settled answer in the platform. `timeout(1)` from GNU coreutils has meant one thing for two decades: exit status **124** means the bound expired, and any other non-zero status is the command's own. Callers, CI systems and shell idioms already know how to read it. Rather than choosing a private convention for what a give-up looks like, wrap the condition loop in `timeout` and inherit both the semantics and the documentation — the answer to "what does 124 mean" becomes a man page nobody here maintains.

**What is bought:** the expiry status, the bound argument, the signal handling, and the meaning of every number the caller might see. **What stays built here:** the retry cadence and the output-trimming, which are this workspace's own preferences and which no general utility provides.

**Against its siblings.** Unlike removing the wait, it works on foreign state. Unlike defining a private expiry status, it costs no design argument and no documentation the operator has to learn — and it is honest about the fact that the sibling's "reserved status" is really just 124 with extra steps.

**What it costs, and this is the objection that could kill it.** `src/loop/wait.ts` argues explicitly and at length that the shim must be plain POSIX `sh` with no external dependency — no `node`, no bundle path — because anything that can go missing "fails as 'command not found' three weeks later and reads exactly like the affordance never existing." `timeout` is precisely such a dependency: it is GNU coreutils, and it is **not present on a stock macOS**, where it ships only as `gtimeout` via Homebrew. The machine this loop actually runs on is a Mac. So the bought convention may be unbuyable on the one platform that matters, and the candidate then degrades to hard-coding the number 124 by hand — which is adopting the *convention* without the *tool*, a materially weaker version of this position that should be judged separately rather than silently substituted.

**Sharpest risk:** feasibility, and it is answerable without asking anyone — either the dependency is reachable on the target platform or it is not.

Ideated by an unattended pass on 2026-08-28 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

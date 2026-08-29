---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility**, and a refutation retires the parent candidate outright rather than shrinking it.

**The belief, stated so it can be false:** every way the shim can be reached is already bounded by something else, so deleting its own bound cannot produce a wait that runs forever.

**Why the product's own code treats this as doubtful.** `DEFAULT_FOR_SECONDS` in `src/loop/wait.ts` is documented as "bounded rather than open-ended on purpose", with the reason spelled out: the shim exists to be written by an unattended session instead of a fixed sleep, and "a wait that can hang forever would trade eight refusals for one wedged firing." That comment is an author who already considered removing the bound and declined. This assumption is the claim that the author was wrong — or that the environment has changed — and it should be treated as the harder position, not the obvious one.

**What would make it false, concretely.** A `Bash` call composed without an explicit `timeout` and defaulting to something generous or unbounded; the shim reached from a script rather than from a tool call, where no harness clock is running at all; or a harness whose timeout kills the tool call but leaves the `sh` child alive. Any one of those is a path where the only bound was the one this candidate proposes to delete.

**Why the evidence available is not enough to settle it.** All six observed give-ups came from calls carrying `"timeout": 400000`, which is consistent with the belief — but six observations from one session are a sample of the paths that happened to be taken, not a census of the paths that exist. The belief is about the latter.

**What it does not settle.** Whether a harness kill is an acceptable *ending* even when it is a reliable one. It produces no trimmed output and no give-up line, so a bounded-but-mute wait may be a worse artifact than an unbounded-but-talkative one. That is a separate judgement, and it belongs to the branch on give-up legibility rather than here.

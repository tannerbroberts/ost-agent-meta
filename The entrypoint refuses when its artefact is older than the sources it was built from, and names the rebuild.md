---
type: Solution
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
killIf: >-
  A firing hits the staleness refusal and cannot act on it, because the rebuild
  command the message names is unavailable in the context the refusal fired in
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Artefact and source timestamps are a reliable enough proxy that ordinary git operations do not produce false refusals]]

**Variation dimension: automated-vs-manual. Position taken: the detection is automated, the repair is left deliberately manual.**

Before doing anything else, the entrypoint compares the artefact's timestamp against the newest source it was built from. If the sources are newer, it exits non-zero with one sentence naming the exact rebuild command, and does not run. It does not rebuild. The detection is free, mechanical and always on; the repair stays a thing somebody chooses to do.

**Why the manual half is the point, not a shortcut.** A rebuild is a write, and this is a product whose whole argument is that a firing does not get to quietly change things underneath the person who left it running. An entrypoint that silently rebuilds is a CLI invocation with a side effect nobody asked for, and it fails in the dangerous direction — a run that appears to have succeeded against the code you thought you had. Refusing is the honest half, and it converts the observed failure from a module-resolution crash three frames deep into a first-line message that says what is wrong and what to type.

**Why this position and not another.** The remove-the-artefact sibling makes the problem unreachable but pays on every startup. This one keeps the fast path completely — a stat of a few files against one artefact, once, before work begins — and gives up only the automatic fix. Against the lifecycle-hook sibling, the difference is where the check lives: a hook fires when the package manager is the one doing the invoking, and the observed failure was a bare `node` invocation, which no hook is on the path of.

**What it deliberately does not do.** It says nothing about whether the artefact is *correct*, only whether it is older than its inputs. A build that succeeded and produced a wrong bundle passes this check, and should — that is a different question with a different answer.

**What it gives up, plainly.** Timestamps are a proxy and they lie in both directions: a checkout, a `git stash`, or any operation that rewrites mtimes without changing content produces a refusal with nothing actually wrong, and a firing that meets a false refusal it cannot explain is worse off than one that meets a clear crash. It also adds a check to the front of every invocation of a CLI this repository's own automation calls six times per script, so a false positive stops all six. And it is the only one of the three that leaves the failure mode fully intact for anything that does not go through the entrypoint.

**What would make this the wrong pick.** If false refusals from mtime churn turn out to be common, this is a worse experience than the crash it replaces, and the remove-the-artefact sibling is the default. If the check is cheap and quiet, it is the smallest change of the three by a wide margin.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface has no grant to run the independent parallel ideators the sweep's `ideation: "blind"` marking asks for. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-02; a human to review.

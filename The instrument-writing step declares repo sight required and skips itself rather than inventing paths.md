---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Whether a pass has repo sight is a good enough proxy for whether its instruments are grounded]]

**The idea.** Gate the activity, not the run. Writing an instrument is the one step that provably degrades without the product repository, so that step declares repo sight required. Without it, the pass does everything else — maps, ideates, surfaces assumptions, repairs hygiene — and skips instrument-writing with a named reason instead of producing commands whose only red is a missing file.

**Why the granularity is the point.** The other two candidates treat sight as a property of the run. It is not: this pass had no repo sight and still did most of its work correctly, because most of the work reads the tree rather than the product. Blocking the run would have cost all of it to protect one step. Reporting at the end would have let the degraded instruments into the tree and then mentioned it. This is the only one of the three that prevents the specific bad artefact.

**And the bad artefact is worse than a wasted turn, which is the argument for building this at all.** A missing-file instrument is indistinguishable, in the tree, from a grounded one. Both are a command in a frontmatter field; both make the solution look answerable; both will be run by someone eventually and both go red. The difference only shows up when a builder tries to use one as a definition of done and finds it says nothing except "create this file." An unattended loop under budget pressure, asked every pass for 64 instruments, will produce those in volume — and each one *removes* its solution from `solutionsMissingInstruments`, so the bucket reports progress while the tree fills with commands that measure nothing.

**Where it fails.** It needs a way to tell the two kinds of red apart in advance, and that is not obviously mechanical. A pass that has repo sight can still write an ungrounded instrument; a pass without it can still write a good one against a mechanism it learned from the tree, as this pass did twice. So "has repo sight" is a proxy for "is grounded", not the thing itself, and gating on the proxy both over- and under-blocks. It also produces a queue that never drains while the config stays unfixed, which is only an improvement if someone eventually reads the reason.

**Compared with its siblings.** Narrower than both and the only one that protects the artefact rather than the run. It composes with "A pass ends by reporting which of its senses were live" — the skip needs somewhere to be reported — and it is redundant with "Every path the config declares is checked when the config is read" only if that check is set to refuse, which the sibling itself argues may be too blunt for an unattended loop.

⚠️ Unvalidated. Agent-ideated by a pass that wrote one such instrument this sitting and said so.

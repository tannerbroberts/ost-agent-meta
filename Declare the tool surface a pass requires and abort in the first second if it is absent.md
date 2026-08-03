---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

A pass states, up front and in one place, the tools it cannot work without. Before any reasoning, it checks that surface and — if the tools are absent — exits immediately with a named, distinctive failure rather than proceeding into work it cannot do.

**The trade it makes:** cheapest possible fix, entirely inside the pass, no new infrastructure. It converts a wasted run into a fast, legible one. What it does *not* do is prevent the run: the compute is still committed, the schedule still fires, and a human still has to notice the loud exit. On a nightly cadence that is three loud exits a week instead of three silent ones — better, but still recurring.

**How it differs from its siblings.** [[Have the scheduler verify the environment before it dispatches a run at all]] moves the same check one layer out, where it can prevent the dispatch instead of aborting it. [[Fall back to the command-line path automatically when the MCP tools are absent]] does not treat the missing surface as fatal at all. This is the strict one: fail fast, fail loud, do nothing else.

**The detail that decides whether it is enough:** the evidence behind this opportunity is *three identical passes, three identical discoveries, and no accumulating signal.* A loud exit that is identical every time still does not accumulate — the fourth toolless run reads exactly like the first. Pairing this with escalate-on-repeat (alert on the first occurrence, escalate on the second, stop scheduling on the third) is what turns a loud failure into a signal, and a human should decide whether that belongs here or as its own candidate.

Distinguishing assumption: that a pass can detect its own tool surface *before* using it. Session `e42cd03d` suggests the opposite is the default — `Unknown skill: superpowers:subagent-driven-development` was only discoverable by calling it.

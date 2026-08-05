---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A tool surface can be confirmed without invoking any of the tools on it]]

A pass states, up front and in one place, the tools it cannot work without. Before any reasoning, it checks that surface and — if the tools are absent — exits immediately with a named, distinctive failure rather than proceeding into work it cannot do.

**The trade it makes:** cheapest possible fix, entirely inside the pass, no new infrastructure. It converts a wasted run into a fast, legible one. What it does *not* do is prevent the run: the compute is still committed, the schedule still fires, and a human still has to notice the loud exit. On a nightly cadence that is three loud exits a week instead of three silent ones — better, but still recurring.

**How it differs from its siblings.** "Have the scheduler verify the environment before it dispatches a run at all" moves the same check one layer out, where it can prevent the dispatch instead of aborting it. "Fall back to the command-line path automatically when the MCP tools are absent" does not treat the missing surface as fatal at all. This is the strict one: fail fast, fail loud, do nothing else.

**The detail that decides whether it is enough:** the evidence behind this opportunity is *three identical passes, three identical discoveries, and no accumulating signal.* A loud exit that is identical every time still does not accumulate — the fourth toolless run reads exactly like the first. Pairing this with escalate-on-repeat (alert on the first occurrence, escalate on the second, stop scheduling on the third) is what turns a loud failure into a signal, and a human should decide whether that belongs here or as its own candidate.

Distinguishing assumption: that a pass can detect its own tool surface *before* using it. Session `e42cd03d` suggests the opposite is the default — `Unknown skill: superpowers:subagent-driven-development` was only discoverable by calling it.

## Definition of done

"Try to confirm a tool surface without invoking any of it"

```
npx vitest run test/runner/tool-surface-preflight.test.ts
```

Green means that on every surface a pass runs on, the full required tool list is confirmed by enumeration with zero invocations of any listed tool. It is red today because no preflight exists — a missing tool is discoverable only by calling it, which is exactly what session `e42cd03d` showed when `Unknown skill: superpowers:subagent-driven-development` came back from the call rather than from a check.

**There is deliberately no partial credit, and the threshold says so.** A preflight that works on two surfaces and silently under-reports on the third is worse than none: it converts a loud absence into a false green, which is "A sweep that cannot read its subject reports a clean result" with extra steps. One surface where enumeration is impossible fails the whole command, because the guarantee is the entire product being bought.

**What a red result buys, and it is not nothing.** If enumeration proves impossible somewhere, the honest fallbacks are already named on this node — call one cheap known tool and read its failure as the signal, or move the check outward to "Have the scheduler verify the environment before it dispatches a run at all", which may see what the pass cannot.

**What green does NOT settle.** It confirms presence, not usability: a tool that enumerates cleanly and then refuses every call, or is present at a schema the caller does not hold, passes this command and fails the run.

## History
- 2026-08-05 unlinked "Try to confirm a tool surface without invoking any of it" — moved under "A tool surface can be confirmed without invoking any of the tools on it" — the belief this test measures now has a node of its own

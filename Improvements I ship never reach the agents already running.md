---
type: Opportunity
status: unvalidated
evidence: assertion
source: 'human:conversation'
created: '2026-07-25'
---
#Opportunity #unvalidated #evidence/assertion

**The need (customer's voice):** "I keep improving the OST-Agent — new MCP tools, better configuration — but the instances already running never see any of it. Each one keeps working with whatever tools and config it launched with, so fixes I shipped days ago still aren't helping the passes that run every day."

**Why it matters:** A product whose agents run continuously and unattended accrues version skew by default: every improvement widens the gap between what exists on `main` and what any live instance actually uses. Until updates propagate, shipping is indistinguishable from not shipping. This is the founder's stated standing priority: continuous update capability — each OST-Agent instance able to take up the latest OST-Agent MCP tools and configuration.

**Reframing note:** The founder stated this as "each instance should be able to *pull* the latest tools and configuration." Pull-on-start is one mechanism; the underlying need is that shipped improvements reach running instances. Litmus test — several distinct directions: pull latest at pass start (`npx @latest`-style), push/broadcast updates to instances, versioned hot-swap at safe checkpoints (see the sibling solution under the parent), scheduled upgrade windows, git-synced configuration. Passes.

**Placement note for a human:** Placed under [[Improving how the agent works means interrupting it]] — that node's pain is the cost of applying a change to a running agent; this one is the prior failure, that changes don't arrive at all. It could also sit under [[I can't leave the process running unattended without worrying]] directly. Flagged rather than double-linked, per the single-best-fit-parent rule.

**Observed corroboration already in this vault (agent-observed, non-external):** five consecutive passes with `npm publish` blocked (`ENEEDAUTH`), so `npx -y ost-agent@latest mcp` — the plugin's own install path — described a package that did not exist at any shipped version (v0.5.0–v0.9.0 on `main`, none on the registry); and a CLI upgrade that silently reopened 18 mapped evidence items (version skew between instance and state). Both are recorded on the root Outcome's pass notes.

Evidence: founder statement in conversation, 2026-07-25.

## History
- 2026-07-25 evidence: (none) → assertion — founder-stated priority; no external party involved; floor rung per the ladder's rule. Observed corroboration exists but is agent-self-observed, so the rung stays at the floor.

---
type: Solution
source: 'WEB:arxiv.org/abs/2605.21997'
created: '2026-08-03'
evidence: assertion
---
#Solution #human-entered #architecture #activegraph #unvalidated #evidence/assertion
[[Replay this vault's whole git history as events and see if the projection matches]]

**Candidate solution (unvalidated). Entered by hand at the operator's direction, 2026-08-03 — not ideated by a pass.**

Rebuild the agent so that an append-only **event log is the source of truth** and the OST is a *deterministic projection* of it, rather than the log being a record kept alongside a tree that is itself authoritative.

**The paradigm.** This is the architecture Yohei Nakajima published as **ActiveGraph** ("BabyAGI 4"), described in *The Log is the Agent: Event-Sourced Reactive Graphs for Auditable, Forkable Agentic Systems* (arXiv:2605.21997; Apache-2.0, `github.com/yoheinakajima/activegraph`). Its inversion of the usual stack is the whole point: you do not start with an LLM and bolt on tools, memory and logging — you start with the log and derive everything else from it. Three primitives:

- **Append-only event log.** Immutable, total order, the single source of truth. It records not only what the agent did but every change to the graph that resulted.
- **Working graph as projection.** The graph holds no independent authority. Replaying the log from zero reconstructs it exactly; any prior state is recoverable by replaying to that event.
- **Behaviors.** Reactive functions bound to graph changes — plain functions, classes, or LLM-backed routines — which emit new events rather than calling each other. No component instructs another; all coordination is through the shared graph.

The claimed properties are **deterministic replay** (any run reconstructible from its log alone), **cheap forking** (branch at any event without re-executing the shared prefix), and **end-to-end lineage** (causal trace from a high-level goal down to an individual model call).

**Why it belongs under this opportunity.** The trust an operator needs before walking away is not "the agent is well-behaved" — it is "I can reconstruct exactly what happened and why, afterwards, without the agent's cooperation." Event-sourcing makes that a structural property rather than a discipline.

**Contrast with siblings.** [[Append-only audit trail the operator can replay]] achieves auditability by *convention* — the agent is disciplined about committing each change with its provenance, and the tree is still the authority. This node makes auditability *structural*: the tree cannot disagree with the log because the tree is computed from it, and no amount of agent misbehavior can produce a state the log does not explain. Against [[Weekly what-changed-and-why digest]] (push, summarized, lossy) and [[Guided dry-run mode before unattended operation]] (trust earned before the fact), this is pull, complete, and retrospective. Its cost is the highest of the four by a wide margin — it is a rewrite of the storage model, not a feature.

## Instructions — how to build this out

Whoever picks this up should treat the following as the shape of the work, not a schedule:

1. **Define the event vocabulary before writing any code.** Every mutation the current MCP surface can perform (`create_node`, `link_nodes`, `append_to_node`, `set_status`, `set_evidence`, `annotate`, `ingest_inbox`) becomes an event type with a closed payload schema. The test that matters: can every existing commit in this vault's git history be expressed as a sequence of these events? If not, the vocabulary is incomplete and the gap is the finding.
2. **Write the projector first, and prove it deterministic.** A pure function `(events[]) -> tree`. Pin it with a test that replays the same log twice and asserts byte-identical output, and a second that replays a prefix and asserts it equals the tree as of that point. Determinism is the contract everything else rests on; if it is not tested it is not true.
3. **Keep Markdown as an output, not the store.** The Obsidian vault stays the human-readable surface, but becomes a rendered artifact of the projection. This is the load-bearing risk: today an operator can hand-edit a node, and a pass can tell a human edit from its own via git. Under event-sourcing a hand edit is a write to a derived artifact and is destroyed on next projection — so the design must either ingest hand edits as events or refuse them loudly. **Decide this explicitly; silently discarding operator edits would be a betrayal of the very trust this node claims to build.**
4. **Port the invariants to behaviors.** The `ost-agent check` rules become reactive behaviors that fire on graph change and emit violation events, rather than a batch pass run afterwards. This is what makes a violation traceable to the event that caused it instead of merely present.
5. **Make forking real, then use it.** The cheapest honest demonstration is to fork this vault at the event before a pass that a later pass had to correct, replay both branches, and diff them. If forking cannot show that, the fork property is decoration here.
6. **Do not port the spend, lock, and cadence machinery into the log.** Those are properties of the *firing*, not of the tree, and folding operational state into the event stream is the most common way event-sourced systems become unreadable.

**Prior art to read before starting:** the paper above, and the `activegraph quickstart` worked example. Adopting the library outright is a live option and probably the first thing to evaluate — the alternative to writing this is not writing it.

**What would make this worth building.** Nothing here is validated. It rests on `assertion`: a published architecture that someone else's agents use, plus the judgement that this tree's auditability is currently a convention rather than a guarantee. Before anyone writes code, the assumption test below should have a result — and note that this node is expensive enough that a refuted test saves considerably more than it costs.

_Addresses: "Trust an unmonitored agent enough to walk away". Unvalidated — human to review._

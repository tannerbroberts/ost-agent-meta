---
type: Opportunity
source: >-
  INBOX:friction/2026-08-01-friction-fifth-straight-scheduled-pass-with-no-ost-mcp-to.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Having the vault is not the same as having the tools, and nothing points that out]]
[[A scheduled run finds out its tools are missing only after it has started]]
[[A helper I installed fails on my own machine's shell, and only running it says so]]
[[A run never states which tools it had, so a degraded pass reads like a full one afterwards]]
[[A pass declares the tools it needs before it starts, and refuses to begin without them]]
[[Every refusal a surface returns is recorded as tree evidence, not just as a failed call]]
[[One surface profile per pass, with the tool set pinned in config rather than inherited]]

**The need (operator's voice):** "I scheduled the same maintenance task I run by hand. Locally it has the full tool surface; on the scheduled surface it silently has none — and I only found out by reading a friction note five passes later. I want a run to tell me what it can actually do before it spends an hour proving it can't."

**Why it matters:** the pass did not fail. It ran the deterministic CLI surface, reported a clean `check`, and exited looking successful — while the actual mandate (map, ideate, surface assumptions over 212 unvalidated nodes) was untouched. This is distinct from "Every run ends blocked on a credential only I hold", where a missing secret is known at the moment it is needed; here the capability is absent and the run has no way to notice.

**Litmus test:** more than one way to address it — a run declares its required tools at start and halts loudly when they are absent; a preflight capability probe written into the run record so a later reader can see what the pass could do; a documented per-surface enablement path; a degraded-mode contract naming what a toolless pass may still legitimately claim; environment-level provisioning that removes the variance. Distinct mechanisms with real trade-offs. Passes.

**Placement note (agent-proposed, needs human confirmation):** nested under "The agent has to guess what resources it's actually working with" as a subset — the parent covers declared project resources and operating constraints, and the agent's own tool surface is exactly such a constraint, discovered the expensive way. A human may prefer it top-level under the Outcome.

**Evidence rung:** `assertion`. Every source below is this agent observing its own tooling — no external party. Floor rung per the ladder's rule. Everything recorded here grounds usability, not demand.

## Standing finding: the claim, and the three shapes it has been observed in

Consolidated 2026-08-23 from ten corroboration sections written 2026-08-02 through 2026-08-20. Each is folded into the shape it was evidence for; git holds the individual entries.

### Shape 1 — the whole surface is absent, and nothing says so (2026-08-01, resolved)

Five consecutive scheduled passes ran with no `ost_*` MCP tools at all. Confirmed via ToolSearch (no `ost_*` tools) and ListPlugins (`ost-agent` not listed), so the MCP server never launched. Root cause converged over four filings, three of them wrong:

- `INBOX:friction/2026-08-01-friction-third-straight-scheduled-pass-15th-16th-17th-wit.md` (kind `blocked`, 12:31Z) — third straight pass with no `ost_*` tools; cause not identified.
- `INBOX:friction/2026-08-01-friction-fourth-straight-scheduled-pass-15th-18th-with-no.md` (kind `missing-affordance`, 14:35Z) — first real cause: `ost-agent-meta` carried no `.claude/settings.json` enabling the plugin. Fix committed.
- `INBOX:friction/2026-08-01-friction-fifth-straight-scheduled-pass-with-no-ost-mcp-to.md` (17:28Z, this node's `source`) — the committed fix cannot work: this surface sets `CLAUDE_CODE_REMOTE_SKIP_SETTINGS_SYNC=1`, so a repo-committed settings file is never applied. Enablement has to happen at the environment level, somewhere the repo cannot reach.

Cost: roughly twenty scheduled passes that produced commentary instead of structure. **The refinement is itself the finding** — the surface gave the agent no way to ask "which of my tools exist here", so it could only infer the answer from the shape of its own failures, one pass at a time.

**Resolved 2026-08-02**, and incompletely: the tools came back and the pass did structural work, but nobody recorded what changed, and nothing was added that would let a future pass detect the same absence. A human should still confirm whether environment-level enablement happened or the surface simply differs run to run. The next differing environment reproduces this silently.

### Shape 2 — the surface is partial, and the split is inverted (2026-08-02 onward, still live)

The variance is finer-grained than "which environment": it is **per-tool, decided at call time, and discoverable only by calling**. Observed repeatedly — `ost_check` refused at the permission layer on five consecutive passes, `ost_flag_humans_required` on three, `ost_status` alongside them — in sessions where every write tool on the same server (`ost_ingest_inbox`, `ost_create_node`, `ost_append_to_node`, `ost_annotate`, `ost_next_work`) worked without a prompt.

**The direction of the split is the opposite of what a safety-minded reader would predict: the tools that cannot change anything are the ones refused, and every tool that mutates the vault is available.** So an unattended pass can write six nodes and cannot ask whether it broke an invariant. That is not a variation in capability so much as an inversion of it.

**The concrete, recurring cost — and the ask this node owes a human.** The sweep brief names exactly two legitimate ways to clear a solution out of `solutionsMissingInstruments`: attach a runnable `instrument`, or, when only real people can answer, `ost_flag_humans_required` it. Of the 25 solutions a pass can see, roughly eleven rest on irreducibly human tests — cold offers, willingness-to-pay probes, story-based interviews. Those must never get an instrument; inventing a spec for "will a stranger accept an offer" is exactly the fabrication the red-now rule exists to prevent. Their only correct disposition is the lane, and **the lane is the one thing this surface cannot set**. They are therefore uncloseable by the unattended loop by construction, and report as debt on every future pass however well that pass does its job. Nothing in the pass's output distinguishes "this pass declined to flag" from "this pass could not".

**For a human, still open:** either grant `ost_flag_humans_required` to the unattended loop — it is the one call on this surface that can only ever *remove* work from compute's reach, which is why the skill hands it to the agent rather than reserving it — or accept the human-lane share of `solutionsMissingInstruments` as permanent debt and stop counting it as outstanding. The middle state spends a firing's attention each hour rediscovering the same wall.

### Shape 3 — the call is made against a tool name the surface does not know

The cheapest instance of the same gap, and therefore a good one to reason from: intent formed against a remembered tool surface, refused only after the call was spent.

- `TRANSCRIPT:e42cd03d-b2a4-44ba-989a-9e01cc368f77` (2026-07-29) — `<tool_use_error>Unknown skill: superpowers:subagent-driven-development</tool_use_error>`. The exact identifier, plugin prefix and all, on a surface that did not have it.
- `TRANSCRIPT:1d62c716-4c49-40ec-84fe-2c849012d3f2` — `Error: No such tool available: mcp__ost-agent__ost_read_tree`.

## The disclosure fix, and the half of it that is still missing

**What was fixed (first seen 2026-08-17).** The unattended pass's own instructions now carry a "What this surface withholds" section naming exactly which `ost_*` tools are absent — `ost_check`, `ost_debt`, `ost_deposit`, `ost_flag_humans_required`, `ost_gate`, `ost_rank_source`, `ost_status` — *before any call is attempted*, with the instruction to do the pass without them and report writes as unverified-by-design rather than as a failure. That is the fix this node asked for on 2026-08-05. The variance has not gone away; it is disclosed rather than silent, which is a materially different cost.

**Disclosure that arrives as an error is still discovery-by-failing.** `TRANSCRIPT:ef6ba23a-db2c-4832-b5e3-aba95040ab8f` (2026-08-20) hit both forms in one session: `Glob` refused with the familiar "you haven't granted it yet" (undisclosed), and `Write` refused twice with "No such tool available: Write. Write is disabled for this session" (disclosed as policy). The disclosed refusal still cost the same two wasted calls, because the firing reached for `Write` before anything told it the tool was off. Only disclosure that arrives *before the first call* saves the turn.

**What is still missing, observed first-hand this pass (2026-08-23).** The pre-call disclosure covers the `ost_*` MCP family **and nothing else**. This firing's own `Glob` against `/Users/tanner/dev/OST-Agent` was refused with "you haven't granted it yet" — no advance notice, one call spent — while `ost_read_repo`, absent from the withheld list, worked and carried the whole pass's repo sight. `TRANSCRIPT:d2c8dbf0-41f7-4517-bc57-88924f735441` (2026-08-23, unattended) shows the identical refusal on `/Users/tanner/dev/OST-Agent/src/ost`. So the fix is real and its scope is one tool family: the built-in file and shell tools are still discovered by failing, and that is now where the remaining turn-cost lives. Extending the withholds list to name the built-ins is the cheap completion of a fix that already works.

## Every observed instance on record

Permission-wall refusals (`Glob` / `Grep` / `ost_read_repo` / `ost_check` / `ost_status` / `ost_flag_humans_required`), several followed immediately by a retry of `ost_ingest_inbox`/`ost_next_work` rather than the refused call — the stall-on-a-wall shape also tracked on "My unattended runs recover from tool errors and retries I never find out about":

`TRANSCRIPT:030e5db3-9414-441f-9221-b4a984c11825` (2026-08-05; `Glob`, `ost_flag_humans_required`, `ost_check`, `ost_status` in a row), `TRANSCRIPT:03b2fe6f-0338-4243-bcb4-5d908a89514f`, `TRANSCRIPT:08f7d98f-24bd-46c0-a5ad-c17d53c4bbca`, `TRANSCRIPT:14c9afa5-ff0d-46b9-ba9b-c068c08eec63`, `TRANSCRIPT:1515b876-9426-4fd8-8259-471f2aba7da1`, `TRANSCRIPT:1a8f25fb-1259-4b80-8b53-32fbfde38e54`, `TRANSCRIPT:1b5a7f48-abaf-4958-8317-d2df1ed37e08`, `TRANSCRIPT:9d3b24f8-d22c-4fc3-80d8-52a861c627f5` (2026-08-18), `TRANSCRIPT:ef6ba23a-db2c-4832-b5e3-aba95040ab8f` (2026-08-20), `TRANSCRIPT:d2c8dbf0-41f7-4517-bc57-88924f735441` (2026-08-23).

Two of these (`14c9afa5`, `1a8f25fb`) additionally hit `ost_read_repo`'s own "no product repos configured" refusal — the tool present but the vault not telling it where the product lives. That is a related but distinct gap, tracked on "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed", and is not folded into this claim.

## Issues
- 2026-08-23 Consolidated ten corroboration sections (2026-08-02 through 2026-08-20) into the standing finding above, and de-duplicated `TRANSCRIPT:030e5db3`, which was recorded twice. No claim dropped; git holds the prior text. **Future sweeps: add a transcript id to the instance list above and, only if it shows a genuinely new shape, a sentence to the shape it belongs to. Do not append a new corroboration section.** Ten passes each added one, and the result was a 19.6KB node carrying one claim.

## History
- 2026-08-05 unlinked "A run declares the tools it needs and halts loudly when they are absent" — re-parented under "A run never states which tools it had, so a degraded pass reads like a full one afterwards" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Every run records the tool surface it actually had" — re-parented under "A run never states which tools it had, so a degraded pass reads like a full one afterwards" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "A degraded pass has its own name and is not allowed to report a clean run" — re-parented under "A run never states which tools it had, so a degraded pass reads like a full one afterwards" — this solution answers that need, not the categories beside it
- 2026-08-23 body edited — Ten corroboration sections, accumulated 2026-08-02 through 2026-08-20, grew this node to 19.6KB in which one claim is restated ten times — and `TRANSCRIPT:030e5db3` is recorded twice, once as a full section and again under "Additional observed instance". This is the same debt two nodes were consolidated for on 2026-08-21, and it is the node the tree's own "Every session leaves an evidence record that restates a need the tree already holds" is about. Nothing is dropped: every distinct fact — the four-filing root cause, the per-tool inversion, the eleven-of-twenty-five uncloseable share, the disclosure fix and its cost, and every transcript id — is folded into the standing finding below, and git holds the prior text. Consolidating rather than appending an eleventh section, because a node whose ask to a human is buried under ten restatements is a node that human will not read.

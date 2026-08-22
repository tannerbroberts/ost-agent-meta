---
type: Opportunity
source: 'agent-run:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Count a source citation in a node's prose as a mapping, wherever in the body it appears]]
[[Give a node a structured list of the sources it rests on, and a tool call to add one]]

**The need.** The skill's own rule for evidence is "reuse, don't duplicate": when a new record corroborates a need already on the tree, append the corroboration to that node rather than minting a second opportunity saying the same thing. Passes here have followed that rule scrupulously for weeks. The queue does not register any of it. Every correctly-handled record stays in `unmappedEvidence` forever, and the count is now **363** — by a wide margin the largest number in the sweep, and the single biggest reason a pass cannot reach `done`.

## The natural experiment, taken from one sweep's own output

This is not inferred. Today's `ost_next_work` returns `unmappedEvidence` alphabetically from the start of the set, so absence from the head of that list is conclusive rather than an artifact of the 25-item cap. Three records sitting within four characters of each other in that ordering behave differently:

| Evidence id | How the tree records it | In `unmappedEvidence` today? |
|---|---|---|
| `TRANSCRIPT:0b98ae8c-…` | not cited anywhere | **yes** |
| `TRANSCRIPT:0d27cebf-…` | carried as the `source:` of "I probe for files that were never there, because nothing hands me the layout of the workspace I am in" | **no — drained** |
| `TRANSCRIPT:0e0cd6f3-…` | cited in the prose of "The agent has to guess what resources it's actually working with", under a dated Corroboration heading with a full `_Source:_` line | **yes** |

`0d27cebf` sorts between the other two and is simply not in the list; the other two are. The only difference between `0d27cebf` and `0e0cd6f3` is **which part of the file names them** — one is a frontmatter `source:`, the other is prose. `TRANSCRIPT:09ec7cd2-…`, cited by name in two separate nodes' corroboration sections, is also still listed.

So the predicate for "mapped" reads the `source:` field and nothing else. And a node has exactly one `source`. Between those two facts, an evidence record can only ever drain the queue by **causing a brand-new node to be created for it** — which is precisely the act the method tells a pass not to perform when the need already exists.

## Why this is a need and not a preference

The rule and the counter point in opposite directions, and a pass has to disobey one of them:

- Follow the method, corroborate the existing node, and the queue reports the work as never done. Repeat for weeks and you get 363 items that no amount of correct work will ever clear.
- Satisfy the counter, mint a new opportunity per record, and you get 363 near-duplicate nodes — the exact debt `near-duplicate` hygiene, `ost_merge_nodes` and the extent-overlap rules exist to prevent.

The incentive as built rewards the second. That nobody has taken it is a fact about the passes, not about the mechanism.

## Why it belongs under this parent

The parent names the general defect — the queue does not drain when the work is done — and already records four mechanisms of it: shipped solutions still asked for instruments, deferred opportunities still counted under-served, category buckets counted as needing direct solutions, and humans-required tests still listed as owing a command. This is the fifth, it is the same shape (a fact the product holds is applied to some analyses and not others), and it is larger than the other four combined.

**How it differs from its siblings, so it is not one of them wearing a new title:** every sibling concerns a **node** whose settled state the queue ignores. This concerns an **evidence record**, which is a different kind of object, drains through a different predicate, and would be fixed by different code. A repair to any sibling leaves all 363 in place.

## Litmus test — more than one way to address it?

Yes, and the candidates disagree about what a mapping *is*: count a prose citation as one; let a node declare several sources through a structured field; let a pass explicitly dispose of a record it has read and judged; or age records out on time and accept that some real needs go unmapped. Different mechanisms, different failure modes, genuine trade-offs. Passes.

## Limits of this finding, stated so it is not over-read

- **The predicate was not read in source.** It lives in `src/mcp/next-work.ts`, which is 74KB and would truncate on a single read; this pass probed its size and did not read it. The behaviour above is established from the tool's own output, which is strong evidence of *what happens* and no evidence of *how it is implemented*. A builder should confirm the predicate before changing it.
- **363 is the count of records, not of unmet needs.** Most of these are transcript friction records whose shapes this tree already carries; a mechanism that drained them would be recording that they were handled, not surfacing new work. Nobody should read a drained queue as more discovery having happened.
- **Whether an operator wants this queue to drain is unasked.** One could argue every record should stay visible until a human has seen it, and that a growing count is the honest signal. That is the design question and this node does not settle it.

⚠️ Unvalidated. Distilled by an unattended pass from its own tool output; no human has confirmed that a draining evidence queue is what they want. First-party observation of this product's own tooling — it grounds feasibility and usability, not demand. No command executed, no result recorded; rung at the `assertion` floor.

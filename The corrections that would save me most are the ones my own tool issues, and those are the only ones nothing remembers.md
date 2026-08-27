---
type: Opportunity
source: 'TRANSCRIPT:a358b10b-e666-44d8-8493-750bff1773e5'
created: '2026-08-27'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed

**The need.** When the harness refuses my call, the next session is told. When *this product's own tools* refuse my call — the tools I use hundreds of times a pass — the next session is told nothing, and pays for the same refusal again. The corrections I most need carried forward are precisely the ones the carrier drops.

This is a subset of the parent need, not a restatement of it. The parent says a lesson learned at 14:00 Tuesday is gone by 09:00 Wednesday, and the corrections ledger was built to answer it. The ledger works. What this node holds is that it works for one class of refusal and is structurally blind to another, so the parent's problem is solved for the harness and untouched for the product itself.

## What was observed

**The ledger's own contents, read first-party on 2026-08-27** (`.git/ost-agent/corrections.json` in this vault): three corrections, total. Every one is a harness refusal — two against `Bash`, one against `Read`. Zero were issued by any `ost_*` tool, across 588 harvested sessions.

**Against a refusal that demonstrably recurs.** The `ost_set_instrument` / `ost_create_node` instrument-grammar refusal has now been recorded in at least three separate unattended firings:

- `TRANSCRIPT:14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0` (2026-08-21) — three consecutive refusals in one session, the agent varying the command each time.
- The pair quoted verbatim on "My instruments are red because a file is absent, not because the behaviour is" (2026-08-21), where a pass with repo sight tried `-t "…"` and then `-t session-id` and was refused both times.
- `TRANSCRIPT:a358b10b-e666-44d8-8493-750bff1773e5` (2026-08-27, the firing immediately before this one) — refused again, same grammar, same reflex.

Three firings, six or more calls, spent rediscovering one fixed rule. That is the exact cost the parent node's census measured for `sleep`, and the mechanism built to stop it did not see any of these.

## Why it cannot see them — read from the code, not inferred

`src/loop/corrections.ts`, `extractRefusals`, gates every candidate on one line:

    const GUARD_MARKER = /<tool_use_error>/;
    ...
    if (!GUARD_MARKER.test(body)) continue;

The module's own comment gives the intent, and the intent is sound: distinguish "a command exited non-zero" (a failure — nothing rejected the *shape* of the call) from "the surface rejected this call" (a correction). But `<tool_use_error>` is a wrapper the *harness* puts on its own refusals. An MCP server's error is returned as plain text and never carries it. The discriminator is therefore not "was this a guard refusal" but "was this refused by the harness", and the product's own guards fall on the wrong side of it by construction.

This is visible in the friction records themselves: harness errors appear as `<tool_use_error>File has not been read yet…</tool_use_error>`, while the same transcripts show `cannot set that instrument on "…"` and `is not an instrument form. The allowed forms are: …` with no wrapper at all.

The second-stage filter would have passed them. `splitRefusal` keeps a refusal that names a permitted form, and `"is not an instrument form. The allowed forms are: vitest-spec (npx vitest run <path>.test.ts)"` names one about as plainly as a message can. It never gets that far.

## Why this bites harder than the harness case

The harness's refusals are generic and few. The product's refusals encode *this tree's own rules* — the instrument grammar, the humans-required lane, the reserved headings, the single-parent edge, the threshold-must-be-a-bar check. Those are the rules an unattended pass most needs to know before composing, they are authored here, and they are changed here. A ledger that carries the host's advice and drops the product's is remembering the least local half.

It also compounds with the parent's own finding: the refusal text already contains the complete correction. Nothing needs to be written better. It needs to be *kept*, and for this class it is not.

## Litmus test — is there more than one way to address this?

Yes, and they are genuinely different products:

- Widen the discriminator so a refusal is recognised by naming a permitted form rather than by its wrapper — cheapest, and risks admitting ordinary command failures the marker was there to exclude.
- Have the MCP server record its own refusals directly at the moment it issues them, never going through transcript archaeology at all.
- State each tool's accepted grammar in its description so the refusal is never provoked — the tree already holds this shape as a candidate elsewhere, for the Monitor tool.
- Emit MCP refusals inside the harness's own error envelope, so one carrier serves both.

Passes: more than one implementation fits, and they differ in who does the work and when.

## For a human to review

**A gate question this node may sit inside.** The parent's 2026-08-02 Issues note records that its own parent, "What the agent learns doesn't accumulate over time", is evidence-debt-gated — "no new siblings until a non-founder artifact cites the row" — and marks it STILL OPEN as of 2026-08-07. This node is a child of a child rather than a new sibling of the gated row, so it is probably outside that gate, and its evidence is machine-captured transcripts plus a first-party read of committed source rather than founder theory. But the ambiguity the note flags is exactly the one that decides it, and the answer is a human's, not this pass's. If the gate is read broadly, defer this node rather than ideating under it.

**No solutions were ideated here.** This pass mapped the need and stopped, deliberately: the four directions listed above are sketched to satisfy the litmus test, not proposed as candidates, and the blind-parallel ideation the ruleset asks for was not available on this surface.

## Provenance

Sources: this vault's `.git/ost-agent/corrections.json` as it stood on 2026-08-27; `src/loop/corrections.ts` read in full through `ost_read_repo`; and the three transcript records named above. Evidence class **observed** — the recurrence is machine-captured from session transcripts with no narrator, and the mechanism is read from committed code. It grounds usability and feasibility, not demand: nothing here says an outside operator wants this fixed, and no test was run.

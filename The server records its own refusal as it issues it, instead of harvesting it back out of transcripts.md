---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A refusal that also records a correction still changes nothing else in the vault]]

**Variation dimension: automated-vs-manual. Position taken: capture is fully automated at the point of refusal; the decision about what a correction *is* stays where it already is and is not re-litigated.**

When an `ost_*` tool refuses a call, it writes the correction itself — at that moment, into the same ledger `src/loop/corrections.ts` already maintains — rather than leaving it in a transcript to be excavated half an hour later. The server is the one party that knows, without inference, what it refused and what it would have accepted: it has the rejection reason in hand, because it just composed it.

**What this removes, and it is the whole argument.** The harvester's job today is archaeology: read a JSONL file, find errored `tool_result` blocks, decide from the text whether the surface rejected a *shape* or the world disagreed with a well-formed call, and split remedy from verdict. Every one of those steps is a guess reconstructing something that was known exactly, once, and then thrown away. Recording at the source deletes the guessing rather than improving it — no wrapper heuristic, no remedy-cue regex, no end-anchoring defence against a guard quoting the caller's own prose back at it.

**Against the sibling that widens the discriminator.** That one keeps archaeology and makes it more permissive, which necessarily re-admits some of what the current marker excludes. This one makes the question not arise for `ost_*` tools at all, while leaving the harvester untouched for harness refusals, which it must keep handling because this product cannot make the harness call anything. So the two are complements as much as rivals, and the honest comparison is cost: this is a change at every refusal site, the sibling is a change at one line.

**What stays manual, deliberately.** The definition of a correction. `splitRefusal`'s rule — a refusal is worth keeping only when it names a permitted form — is a judgement someone made and tuned against real messages, and it should keep governing both carriers so the ledger does not end up with two notions of its own unit. A tool refusing without naming an alternative should record nothing, exactly as today.

**What it costs.** Every refusal path becomes a write path, in a codebase whose whole discipline is about which surfaces may write what. That is the objection to take seriously: a refusal that also writes is no longer a pure rejection, it has a side effect, and a malformed call could now leave a trace even though it changed nothing else. The ledger lives outside the working tree (`.git/ost-agent/`, per `state.ts`, so MCP commits do not sweep it up), which contains the blast radius but does not make the objection go away.

**Its distinctive failure mode.** The ledger fills with the agent's own noise. Sixty refusals in one pass — a session probing a boundary — all get recorded, where the transcript-harvesting route would have folded them by remedy and capped them at 25. Folding still applies, so the cap holds; what changes is that self-inflicted churn is now recorded live rather than filtered by the quiet window. This product already has a node about that shape, "The friction channel fills with my own typos, so the signal I wanted is buried", and this candidate walks straight into it.

Ideated by an unattended pass on 2026-08-27 against the assigned dimension. **Not blind:** all three candidates under this opportunity were composed in one context by one author, because this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

## Definition of done

"A refused call writes one ledger line, no node file, and no commit"

    npx vitest run test/mcp/refusal-side-effect-bounds.test.ts

The bar that command is settling: a refused call adds exactly 1 corrections-ledger line, 0 node files and 0 commits — the last two being the regression half, green today and required to stay green, because the risk this candidate carries is not that recording fails but that it stops a refusal being inert.

The test title is quoted rather than wikilinked on purpose — its one backlink belongs to its parent assumption, "A refusal that also records a correction still changes nothing else in the vault".

**What a green does not buy.** It bounds the side effects of one refused call; it says nothing about ledger volume across a real pass, which is the noise risk this candidate names against itself, and nothing about whether anyone wanted refusals recorded at all.

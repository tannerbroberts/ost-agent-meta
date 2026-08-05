---
type: Solution
status: unvalidated
evidence: assertion
source: 'agent-ideation — generalized from tetrix-ost commits bfa741b, 2328e61'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Does a briefing node change which node a builder actually opens first]]

**The idea.** One node, always at the same address, holding the agent's current reading of what to do next and why — rewritten (append-only, so the history is the record) at the end of every pass. Not buried in root annotations. Not a decision; a briefing.

**Why this is the cheapest thing that could work.** Both running instances already produce this content. They just produce it in the wrong place. The tetrix agent's final act was a 400-word annotation on the root Outcome titled *"What a builder should build next — surfaced, explicitly not decided"* — a genuinely excellent piece of prioritization reasoning, appended to the bottom of a node that already carried six other long annotations about unrelated concerns. The root Outcome has become an undifferentiated queue of things a human needs to decide, and the one thing a builder most needs to read is at the bottom of it.

Give that content its own address and it becomes findable. Nothing else in the tree changes.

**What good looks like — and the tetrix agent modelled it well enough to copy.** Its briefing had four parts: the highest-leverage build with the reasoning that makes it checkable; an explicit statement that the highest-*leverage* build is **not** the highest-*information* action (interviewing five real players was, and it said so); the small number of cheap human decisions that gate everything; and a warning about its own bias. That last part is the one worth mandating. Left to itself an agent will steer toward work it can do alone, and the briefing is where it should be made to declare that pull so the reader can discount it.

**Relationship to the ranking solution.** These are complements that survive each other's failure. Unblocking-leverage ranking is structural and auditable but says nothing when a tree's tests are independent. A written briefing carries judgement a graph cannot, but is only as good as the agent writing it. Shipping the briefing first is defensible on its own: it needs no schema change, no declarations on existing nodes, and it puts today's already-good output somewhere a builder will find it.

**Where this fails.** A briefing that says the same thing five passes running is noise, and the operator learns to skip it — the same fate the root annotations just suffered. It probably needs to say what *changed* since the last one, not just what is true.

⚠️ Unvalidated. Proposed by an agent, from an agent's behaviour.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## The predicted failure was noise. The observed one is collision — 2026-07-26

The **Where this fails** section above named one risk: a briefing that repeats itself
becomes noise and the operator learns to skip it. Seven passes in, that risk has not
materialised — every rewrite has said what changed, and the briefings have been read and
acted on.

The failure that did materialise is not in that paragraph at all. **Two passes read the
same briefing hours apart and both built the thing it named**, because a briefing that
names work has no way to say the work has been taken. Full account, with times, on
[[Two agents sharing my vault can trample each other]]. Cost: one build pass, discarded.

**Why this design invites it specifically.** The briefing is rewritten each pass and
carries no state between readers. Its "if something must be built" clause is written to
be actionable by whoever picks it up next — which is exactly right for one reader and
exactly wrong for two. The tetrix briefing's clause had stood for two passes; the first
pass to act on it shipped at 02:56Z, rewrote the briefing, and by then the second pass
had been holding a stale clone since 00:47Z and never re-read it.

**What this does NOT imply.** Not that the briefing was a mistake — it is the most
consistently acted-on artifact either vault has produced. The gap is that it is a
*statement of intent* with no *record of uptake*: nothing says who is on it, since when,
or against which commit. Both things it lacks are things a second reader needs and a
single reader never notices missing.

Left as an annotation rather than a proposed change. What to do about it — a claim, a
lease, one-writer-per-repo, or simply accepting that a stale reader wastes a pass
occasionally — is a decision with real trade-offs, and the party that just lost a pass to
it is not a neutral one.

## Definition of done

[[Does a briefing node change which node a builder actually opens first]]

`npx vitest run test/ost/next-build-briefing.test.ts`

The spec asserts the briefing resolves to one stable address across passes and that each rewrite preserves the prior reading rather than overwriting it — the history being the record is the node's own claim. Red today because no standing briefing node exists and the content is still going into root annotations, which is precisely the failure this node was written about.

**What a green here does not settle.** Two things, and the second is the more important. First, whether a builder opens a different node because of it — that is the humans-required test and no spec sees a reader's attention. Second, and unaddressed by this instrument: the failure that actually materialised was not the noise the node predicted but **collision** — two passes read the same briefing hours apart and both built what it named, because a statement of intent carries no record of uptake. A stable address and preserved history do nothing about that. Whoever builds this should read the 2026-07-26 section above first and decide whether uptake belongs in the same change.

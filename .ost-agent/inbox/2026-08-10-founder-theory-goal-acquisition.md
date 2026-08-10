# Founder theory: goal acquisition as the capability, not filtering on one goal's altitude (2026-08-10)

Spoken in session by the founder. Evidence class: **assertion** — founder theory,
recorded verbatim in substance for later distillation. No evidentiary weight until
laddered.

**The claim.** The founder does not want OST-Agent to "mindlessly filter on the single
central goal's abstraction level." The thing people can do that AI has not been proven
for is **goal acquisition**, and he wants it built into this tree system. His stated
mechanism for making progress on anything: an agent needs proper autonomy to (1) make
a guess as to how the world works, (2) test that guess, (3) stake a claim on untested
ground, and (4) see if it sticks. The four together — not any one alone — are what he
means by goal acquisition.

**Session-context observations recorded alongside (agent's, same rung):**

1. The tree already holds the *decomposition* half of this under the altitude branch
   ("The goal I care about is too far from anything I can act on this week" → "I aim
   at a goal I can afford to chart, not the one I actually want", with sub-outcomes /
   milestone / contribution-estimates / named-darkness solutions beneath). All of it
   is unvalidated founder theory, and the lane is evidence-debt-gated: no new
   siblings until a non-founder artifact cites the row. This note is another founder
   artifact and does not lift that gate.
2. The *acquisition* half is documented in the product only as a prohibition: "an
   agent must never originate the mandate it steers by" (`src/mcp/setup.ts:12`),
   `set-outcome` is human-CLI-only, and `setOutcome` is on the genome's not-genes
   list. The sanctioned escape hatch — flag a mis-formed outcome as a question for
   humans (`ruleset.ts:137`) — is prose-only; no tool implements it.
3. Of the founder's four steps, the product today has (1) and (3) structurally
   (everything agent-made enters `#unvalidated` and nothing agent-reachable removes
   the tag — a stake, honestly labeled) and lacks (2) and (4) by design: DEC-3, "an
   agent that answers feasibility questions by executing tests against its
   environment unattended," is recorded as deliberately unbuilt
   (`docs/reference/v1-readiness.md:1341`), and validation of agent ideas is
   human-only. The `#Unknown` layer gives it wanting-to-know beneath a fixed mandate,
   which is curiosity, not acquisition.
4. Open collision for a future pass to map rather than resolve: does this claim argue
   for (a) building goal acquisition *beneath* the mandate — agent-formed
   sub-outcomes plus unattended claim-testing, i.e. shipping DEC-3 and growing the
   altitude branch — or (b) relaxing the never-originate-the-mandate invariant
   itself? (b) is a mandate change and is the founder's alone; nothing in this note
   authorizes it. The distillation should keep the two separable instead of letting
   the exciting reading swallow the buildable one.
5. Adjacent unresolved human decision already flagged in the tree: the sub-outcome
   vs milestone duplicate (two instruments about to build one intermediate layer
   under two names; the deciding question is whether nesting is recursive).

**For a future pass:** distill — the candidate opportunity is something like "I can't
trust the agent with a goal unless it can acquire sub-goals and test its own guesses,"
which serves the external-returning-operators mandate through operator trust in
unattended autonomy. Check it against the existing altitude branch before creating
anything: this may be evidence for that branch's parent rather than a new limb.

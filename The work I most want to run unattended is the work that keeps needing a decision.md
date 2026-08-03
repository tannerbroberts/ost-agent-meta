---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:16e9596b-7c8f-445b-a8ff-f822ed211ea5'
created: '2026-08-02'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

One captured session stopped to ask a human eight separate times, and its questions were not trivia — what happens to the published package, how the server should launch once a dependency is gone, whether a severed ingestion path should be closed one way or another, whether to fix a violation the plan itself forbade. Another session asked seven times. These are the decisions that determine what the product becomes, and none of them could be settled by the agent alone.

That is the bind. The work worth automating is the work with consequences, and consequence is exactly what makes a question un-delegatable. An unattended run either stalls at the first fork or takes the fork itself, and the second option is how an agent quietly becomes the person deciding what the product is.

**The need:** I want a run to keep moving through the decisions that don't need me, and to bank the ones that do without stopping dead.

More than one way to address this: let a pass queue its questions and continue on everything independent of them, pre-authorize whole classes of decision in advance, have the agent proceed under a stated assumption and mark what would change if the answer differs, or split the work so the decision-heavy part is separated from the mechanical part rather than interleaved with it.

## Provenance

Distilled from `TRANSCRIPT:16e9596b-7c8f-445b-a8ff-f822ed211ea5` — a session whose entire friction record is eight clarifying questions, with no tool errors at all. Corroborated by `7e982096` (seven questions), and single questions in `470cb94a`, `748498c4`, `424486ec` and `0d27cebf`.

## Corroboration — sixteen stops across eight sessions (unattended sweep, 2026-08-03)

Of twenty-two mechanically-captured sessions read this pass, **eight had to stop and ask a human something**, producing sixteen `AskUserQuestion` events. What the questions were about matters more than the count, because none of them is a question a human was uniquely qualified to answer — they are places the agent had no standing to choose:

- **Scope of its own mandate** — `470cb94a`: *"The new criteria describe mechanisms that don't exist yet (a scheduler, a spend ceiling, a stuck-detector). Should this turn ship the spec only, or also build the cheap ones?"*
- **Irreversible or outward-facing acts** — `7e982096`: *"What happens to the already-published `ost-agent` package on npm?"*; `87a025f8`: whether a draft PR made obsolete by a later commit should be closed.
- **Which of two defensible routes to take** — `e42cd03d`: *"Should OST-Agent do its own web discovery, or delegate it to the host agent?"*; *"How should the committed merge conflict in `src/cli/index.ts` be resolved?"*; *"How should the keyless-search work land on the real origin/main?"*
- **How the loop itself should be driven** — `0d27cebf`: *"How should the loop be driven?"*; `a615eb46`: *"This loop stops when you close this session. Set it up as a cloud schedule instead so it keeps running?"*

Session `7e982096` is the extreme case and worth naming on its own: **its only friction was clarifying questions — seven of them, no tool errors at all.** A session that ran cleanly by every mechanical measure and still could not finish without a person seven separate times. That is this opportunity in its purest form: the blocker was not capability, it was authority.

`424486ec` and `748498c4` round out the eight.

_Source: the eight `TRANSCRIPT:` records named above, read in full this pass — observed behavior from the agent's own transcripts. Grounds usability, not demand. Corroboration only; the node's rung is unchanged._

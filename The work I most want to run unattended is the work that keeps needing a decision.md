---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:16e9596b-7c8f-445b-a8ff-f822ed211ea5'
created: '2026-08-02'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[One migration stopped me seven times, because settling the policy once never settled the rest]]
[[Answering one question costs me three turns, because I have to fix its options before I can reply]]
[[A run has no authority to decide anything, so every fork is a full stop]]

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

## Corroboration — a ninth session, and this time the fork was about this tree's own gate (unattended sweep, 2026-08-03)

`TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9` is the only new evidence item this pass captured, and one of its three friction events is an `AskUserQuestion`: *"What should the build loop do when the tree's own gate refuses a candidate?"* — offered with a recommended option and a `Gate policy` header, which is what a session does when it has already worked out the answer it prefers and still has no standing to take it.

That makes nine sessions and seventeen recorded stops. It is also the sharpest instance yet, because the question is not about the world outside — it is about **the governance of this vault**: when the evidence-debt gate refuses a candidate, does the loop build something else, build the blocker, or stop? An agent that answers that on its own authority is not automating the build loop, it is amending the rules the build loop exists to obey. Every mechanism named in the body has to survive that case, and the two that let compute proceed (pre-authorized classes, proceed-under-stated-assumption) are the two it strains hardest.

_Source: `TRANSCRIPT:3d729ebc-348f-4d45-8f3c-25df1de8fbc9`, read in full this pass — observed behavior from the agent's own transcript. Grounds usability, not demand. Corroboration only; the node's rung is unchanged._

## History
- 2026-08-05 unlinked "A question queue the run banks and works around, instead of stopping at the fork" — re-parented under "A run has no authority to decide anything, so every fork is a full stop" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "A standing authority contract naming which classes of decision compute may take alone" — re-parented under "A run has no authority to decide anything, so every fork is a full stop" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Take the fork, state the assumption, and price the reversal" — re-parented under "A run has no authority to decide anything, so every fork is a full stop" — this solution answers that need, not the categories beside it

## Observed corroboration — 2026-08-05 sweep

Five machine-recorded stops, and they fall into two kinds that a solution here should not treat alike.

**A guard that worked, and had nobody to ask.** `TRANSCRIPT:5de6e49b-d840-4fba-9549-206d3b0d7276` (2026-08-05, the most recent trace in this batch): `ExitWorktree` refused with *"Worktree has 2 commits on worktree-discovery-eyes. Removing will discard this work permanently. Confirm with the user, then re-invoke with discard_changes: true — or use action: keep."* The refusal is correct and the alternative is spelled out. It still ends an unattended run, and the two commits are now stranded in a worktree the run may neither discard nor clean up.

**Taste questions with no safe default.** Four sessions stopped to ask the operator to choose a framing rather than to authorise a risk:
- `TRANSCRIPT:2c1b611a-ae7e-4191-aefe-b489c631a115` — how metacognition should sit relative to the external-operators metric
- `TRANSCRIPT:dcdaebdb-ffd9-4944-973b-cf0b8e1113c4` — which of two renderings to put in a script
- `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f` — which environment a vault should be
- `TRANSCRIPT:87a025f8-c6b0-474f-9a13-0b5ec5c922ea` — whether an obsolete PR should be closed

The split matters because the obvious fix for one is wrong for the other. A stated default that stands while the operator is away is a reasonable answer to the second kind, where every option is recoverable and the cost of guessing wrong is a rewrite. It is the wrong answer to the first, where the whole point of the stop is that the action is irreversible. Any candidate solution beneath this opportunity should say which kind it addresses; one that claims both is probably answering neither.

## Issues
- 2026-08-07 Near-duplicate of "A run has no authority to decide anything, so every fork is a full stop" — proposed merge, not executed. Both state that unattended work is precisely the work that keeps hitting decisions compute is not permitted to take, so the promise of leaving it running defeats itself. That node already carries three solutions ("A question queue the run banks and works around, instead of stopping at the fork", "A standing authority contract naming which classes of decision compute may take alone", "Take the fork, state the assumption, and price the reversal"); this node carries none. Recommended: merge this INTO "A run has no authority to decide anything, so every fork is a full stop", folding in this node's framing of the irony — the value and the blocker are the same property of the work — which the survivor states mechanically. Not executed here for want of body sight; see "The repair I am asked to make requires rewriting prose no tool will show me". First-party corroboration from this pass: session 2a4bcf6e is an unattended firing that raised an AskUserQuestion ("The data doesn't support a delete-and-rebuild. How do you want to proceed?") with nobody present to answer it.

---
type: Opportunity
source: 'TRANSCRIPT:42dcb7b4-f01b-40bc-a211-ed4a44a74fd3'
created: '2026-08-04'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Every forced choice carries an open field, and a written answer is first-class]]
[[Ask the open question first, and offer options only once the frame is agreed]]
[[State the decision the run is about to take and invite correction, instead of enumerating choices]]

When the run stops to ask me something, the choice it offers me is not the choice I am actually facing. I cannot pick an option, so I reject the question and explain what it should have asked. It asks again, sharper but still wrong, and I reject it again. The decision itself took me a second; getting the run to accept it took three exchanges.

**What was observed.** In `TRANSCRIPT:42dcb7b4-f01b-40bc-a211-ed4a44a74fd3`, two `AskUserQuestion` calls were both answered `permission_denied` — not a refusal to decide, but a refusal of the question's shape. The recorded reason on the first is "The user wants to clarify…", and the second question is a visibly narrowed re-ask of the first ("What should the appended tests be allowed to do to the build gate?" → "When the instrument's input is the code itself … May the runner file that result…"). The operator was not withholding an answer. They were rewriting the question, twice, before they could give one.

**Why this is its own need.** The tree already holds the need to be stopped *less often* — that is [[One migration stopped me seven times, because settling the policy once never settled the rest]], and the solutions under it bank, budget, or defer the asking. Every one of them assumes that when a question does get asked, answering it is cheap. This observation says it is not. A question with the wrong options is worse than no question: it spends the operator's turn and returns no decision, and banking or budgeting a malformed question only changes when the operator has to fix it.

**The distinguishing test.** More than one thing could address this — offering a free-text escape beside the options, asking the open question first and only offering options once the frame is agreed, or having the run state the decision it is about to take and invite correction rather than enumerate choices it guessed at. So it is a need, not a solution wearing one.

⚠️ Unvalidated. Distilled by an unattended pass from one recorded session — the operator's own behaviour, not their stated account of it. Two rejections in one session is a sighting, not a rate.

## Corroborating session (2026-08-04)

- `TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc` — a `permission_denied` recorded **against an `AskUserQuestion` call**: *"The user doesn't want to proceed with this tool use… the user said: The user wants to clarify…"*. The human rejected the question itself rather than answering it, and the run then asked a second, reframed question in the same session.

This is the cleanest capture of this need so far, because it is the mechanism showing rather than the complaint. The rejection is machine-recorded on the question tool, so the cost is countable: one question asked, one rejection, one re-ask — three turns to obtain one answer, exactly as the title claims. It also shows the failure is not about option *wording* alone; the human's stated reason was that the framing needed clarifying before any of the offered options could be picked.

Evidence class is observed behaviour of this agent using its own harness — usability, not demand.

## First machine-captured instance — the human rejected the question rather than answering it

`TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc` (2026-08-04) records the sequence this node describes, in order, with no narration between the events:

1. `clarifying_question` (AskUserQuestion) — *"How should the lineage prefix handle long node titles?"*, offering options beginning *"Abbreviate ancestors, target in full — each ancestor clipped to …"*
2. `permission_denied` (AskUserQuestion) — *"The user doesn't want to proceed with this tool use. The tool use was rejected… To tell you how to proceed, the user said: The user wants to clarify…"*
3. `clarifying_question` (AskUserQuestion) — a different question entirely, about what should happen to the loser of a duplicate merge

Until now this node rested on the founder's account of the experience. This is the same event captured mechanically, by a channel with no view about it: **the question was not answered, it was refused**, and the reply the human did give was a correction to the framing rather than a choice among the options offered. The run then spent a further turn asking again.

**What it costs, precisely.** Three turns of the human's attention were spent, and exactly zero of them were the one-turn act of picking an option. The node's title says "three turns" and this instance is a literal three.

**What it does not establish.** One instance. It says the failure mode is real and is now observable in a channel that captures it without anyone deciding to file it; it says nothing about how often it happens, and a single `permission_denied` on an `AskUserQuestion` is a thin signal — a person can reject a prompt for reasons that have nothing to do with its options being wrong. What would make it countable is that the pattern is mechanically detectable: a `clarifying_question` followed by a `permission_denied` on the same tool is a shape a rule could scan for across the whole transcript corpus. Across the twenty-three records read on 2026-08-04 this shape occurs once, which is the honest denominator.

_Provenance: `TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc`, machine-captured from a session transcript, no narrator. Observed behavior of this product's own agent and its operator; grounds usability, not desirability. Unvalidated — for human review._

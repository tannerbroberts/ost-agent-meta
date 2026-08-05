---
type: Solution
source: 'agent-ideated:2026-08-02-maintenance-pass-2'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A model reading a whole session finds friction that a pattern scan structurally cannot]]

**The idea.** Instead of scanning a transcript for error strings, have a model read the whole session and answer a small fixed set of questions about it: where did the agent change its mind, and what changed it? What did it try, abandon, and not come back to? Where did it repeat itself without noticing? What did it believe at the start that it did not believe at the end? The answers, with quotes, become the evidence item. The mechanical scan stays where it is; this reads the same file for a different thing.

**Why this is not "Post-session transcript harvester".** The harvester already reads every transcript — and produces `tool_error`, `retry`, `clarifying_question`. Those are the three things a regex can find. Its output over 24 sessions is on the parent node: 82 events, zero conceptual items. The input was never the limitation; the reader was. This candidate changes the reader and leaves the plumbing, which is also why it is cheap to try — the corpus already exists and can be read retrospectively today.

**Its distinctive advantage over self-report.** It is not the confused party's account of its own confusion. A reader that was not in the session has no session to defend, sees the whole arc including the parts the agent forgot, and can be pointed at the sessions that went *worst* — precisely where "End-of-session retrospective the agent must write before the session closes" is weakest.

**The trade it asks the operator to accept, and it is a real one.** Every session gets read by a model, which costs money proportional to how much the product is used — the only candidate here with that property — and this vault's operator has already recorded that the credential-and-cost path is the binding constraint on unattended work ("Every run ends blocked on a credential only I hold"). Worse, the output is an interpretation, which is precisely the kind of claim this tree's believability ladder is built to distrust: a model's account of what an agent was confused about is `assertion` about `observed` raw material, and a pass could quietly launder the one into the other. Any version of this that ships needs the quotes attached, so a human can check the reading against the transcript.

⚠️ Unvalidated. Agent-ideated during the 2026-08-02 maintenance pass. Compare against its two siblings before any of them is built; none has a recorded result.

## Definition of done

"Blind-rate a model's reading of five already-harvested sessions"

`npx vitest run test/adapters/transcript-model-reader.test.ts`

The spec asserts the guard this node names as the condition of shipping at all: every filed item carries a verbatim quote, and each quote is locatable in the transcript the item claims to come from. That is the mechanical half of "a human can check the reading against the transcript". It is red today because the transcript adapter only pattern-scans for `tool_error`, `retry` and `clarifying_question` — there is no model-reading path for the spec to call.

**What a green here does not settle.** Quote-traceability stops an interpretation being laundered into observed material; it says nothing about whether the interpretation is any good. Whether a model reading a whole session surfaces anything a regex missed — the entire premise, given the harvester's 82 events and zero conceptual items over 24 sessions — is the blind-rating, and that needs a person who was not in the session. The cost objection the node raises is also untouched: a spec cannot price per-session model reads against an operator whose binding constraint is already the credential.

## History
- 2026-08-05 unlinked "Blind-rate a model's reading of five already-harvested sessions" — moved under "A model reading a whole session finds friction that a pattern scan structurally cannot" — the belief this test measures now has a node of its own

---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Every threshold and instrument the imperative checks reject today is still rejected by the schema patterns]]

**The belief, stated so it could be false:** the threshold and instrument grammars can be expressed as JSON Schema `pattern` constraints that reject every input the current imperative checks reject — no input that is refused today becomes acceptable.

**Why it could be false, and why this is the risk that matters.** A regular expression is strictly less expressive than arbitrary code. The threshold check refuses "a restated sentence" and requires "a comparator next to the number it commits to" — a judgement about whether a bar is actually fixed, which may not reduce to a pattern. The instrument check rejects shell metacharacters and matches one anchored command form; that is closer to pattern-shaped, but "closer" is not "equal". If the translation loses precision it will lose it in the permissive direction, because a pattern written to accept all currently-valid inputs will tend to accept some currently-invalid ones too. That failure is silent: a threshold nobody can read as a bar gets written, and the whole reason the check exists — that a bar a person interprets after the run can be read as a pass whatever comes back — is quietly restored.

**Risk category:** feasibility, with a safety consequence.

**What this assumption is NOT.** It is not the claim that the refusal messages survive the move. Message quality is this candidate's other admitted cost and is a separate belief; a human may want it as its own node.

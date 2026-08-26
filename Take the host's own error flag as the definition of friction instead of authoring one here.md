---
type: Solution
source: 'TRANSCRIPT:98dcaba0-5cd8-4e56-8360-55b58a655cd8'
created: '2026-08-26'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: bought-vs-built. Position taken: adopt the upstream signal as it is, build nothing that judges.**

The transcript this harvester reads is produced by the host harness, and the harness already marks which tool results it considered errors — that flag travels in the record alongside the text. This candidate stops classifying entirely and reads that field: an event is friction when the host said the call failed, and is not friction otherwise. The `retry` inference, which exists only because nobody wanted to depend on the upstream field, is dropped along with every rule authored here.

**Why adopting beats authoring for this particular judgement.** The host is the only party that knows whether a call succeeded — it is the one that ran it. Every rule written on this side is a guess at that fact from its shadow: the same tool name appearing twice, an error-shaped string in the output. The record captured this pass is what that guessing looks like when it is wrong, and the correct answer was present in the source data the whole time.

**Against the siblings.** Deleting the `retry` class removes the bad inference but still leaves this side deciding what counts as an error, from the text. A manifest adds a second locally-authored rule on top of the first. This is the only candidate that reduces the number of judgements made here to zero.

**What it costs, and it is the real risk.** It hands the definition of friction to a surface this project does not control and cannot version. If the harness changes how it flags errors, or stops emitting the field, the channel degrades silently — and a channel that silently stops recording pain is worse than one that records too much. It also inherits the host's opinion wholesale: a refusal the harness treats as a normal outcome will never file here, even when it is exactly the friction the operator wanted to see. This workspace's own standing corrections are refusals of that kind.

**What would make this the wrong pick.** If the flag is not actually present in the captured records, or is present but coarse enough that permission refusals and genuine failures share one value, then there is nothing to adopt and this collapses into the sibling that deletes the class. That is a fact about the stored records, checkable before choosing.

Unvalidated — a human to review.

---
type: Opportunity
source: >-
  agent-observation:autonomous-loop-2026-07-26-tenth-pass — ost_annotate called
  with `note` instead of `issue`, fourteen destroyed annotations across both
  live vaults
created: '2026-07-26'
evidence: assertion
---
#Opportunity #evidence/assertion
[[A call the tool should have refused is permanent, because append-only cannot take it back]]
[[A malformed call lands before anything checks it, and only reading back the file says so]]

**The need, stated as an operator would.** *If I call a tool wrong, I need it to refuse me. In an append-only vault a bad write is forever, so 'it went through' is not the reassurance it sounds like.*

**What happened, observed rather than reasoned.** A pass called `ost_annotate` with `note` instead of the declared `issue`. The tool's schema says `required: ["title","issue"]` and `additionalProperties: false`, so the call was invalid on its face. `runTool` handed the object straight to `run` anyway; `input.issue` read as `undefined`; the string **"undefined"** was appended to the node's Issues section; and the call **printed success**. The note itself was never written anywhere. Because the vault is append-only, the line can be annotated but never removed — the content is unrecoverable.

**Scale, counted rather than estimated.** Fourteen such lines across the two live vaults — 8 nodes in this one (dated 2026-07-26) and 6 in the tetrix vault (dated 2026-07-24). Several different passes, over three days, each losing whatever it was trying to file. Nobody noticed, because the only symptom is a line that says `undefined` in a section a reader skims.

**Why this is the sharpest evidence in this tree about its own central claim.** The package describes itself as *incapable of destructive action by construction*. That is true of the tool **surface** — no delete tool exists, and none was involved. The destruction came through a *constructive* tool holding an argument nobody checked. The allowlist answered *which tool may run* and nothing answered *with what*. A guarantee about which verbs exist is not a guarantee about what they are handed, and this tree had been treating the first as though it covered the second.

**Why it ladders to the outcome.** The outcome counts operators who come back for a second pass. An operator whose filed insight silently becomes the word "undefined" loses the thing they were using the product to keep — and finds out, if ever, long after they could reconstruct it.

**Litmus test — more than one way to address it?** Yes: validate every call against the schema the tool already declares (what v0.17.0 did); make the vault reject a write whose content is empty or literally `undefined`, wherever it came from; echo back what was written so a caller sees the damage immediately; or accept loose input and coerce, which is the option this finding argues against.

**Rung `observed`.** Not a founder assertion and not model ideation: fourteen instances are on disk and in git history, and the reproduction is one command. It is still our own system observed by itself, and no outside operator has hit this — that they *would* is the inference, not the observation.

## Issues
- 2026-07-26 **Correction to the count above, same pass (2026-07-26).** The body says fourteen destroyed lines. The accurate figure is **21 lines across 16 nodes** — 6 lines in 5 nodes here, and **15 lines in 11 nodes** in the tetrix vault. The first number came from `grep -rlc` over files *containing the word* `undefined` anywhere, which both under-counted nodes with several destroyed lines and mixed in nodes where the word appears in ordinary prose. The correct query counts lines matching the annotation shape. — The v0.17.0 changelog carries the wrong figure and is already published; this annotation is the correction of record, and the fix it describes is unaffected. — **Worth noticing rather than burying:** this happened inside the pass whose entire subject was a tool reporting something it had not actually checked, and it is the same error one level up — a number produced by a query that answered a near-miss of the question asked, reported without stating what the query matched. It was caught only because a later step happened to recount. Neither the changelog nor the node body would have shown a reader anything suspicious.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
- 2026-08-05 unlinked [[Validate every tool call against the schema the tool already declares]] — re-parented under [[A malformed call lands before anything checks it, and only reading back the file says so]] — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked [[Refuse a write whose content is empty or literally undefined]] — re-parented under [[A malformed call lands before anything checks it, and only reading back the file says so]] — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked [[Echo the written line back so a bad write is visible immediately]] — re-parented under [[A malformed call lands before anything checks it, and only reading back the file says so]] — this solution answers that need, not the categories beside it

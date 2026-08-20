---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A builder's self-filed disconfirmation is honest often enough that a human acts on it instead of re-deriving it]]

**Variation dimension: who decides — the builder's judgement, carried verbatim, never promoted.** The builder is the only party that saw *why* the assertion failed: it wrote the replay, read the numbers, and knew the bar. Today that judgement is a paragraph in `last-report.txt` that the loop's postflight explicitly overrides ("regardless of what the report above says"). This candidate gives it a structured shape — a `disconfirmation:` block naming the test, the pre-committed bar, the observed value, and the builder's claim that the red is *by design* — which the loop appends to the instrument's node as a clearly labelled, non-reserved section, and which discovery's next pass reads as an input to proposing `deferred`.

**What it is not, stated first because it is the risk.** It is NOT a `## Results` line. A result is a human's, by construction (`src/ost/results.ts`, "it stays human-only"), and this candidate does not touch that: the disconfirmation clears no gate, mints no permit, and changes no status. It is an annotation with provenance, one rung up from the report file nobody reads. The kill is still proposed by discovery and made by a human; what changes is that the proposal has the builder's numbers attached instead of having to be reconstructed from a transcript.

**Against its siblings.** The only candidate that preserves *why* the idea lost — "After N builds leave an instrument red…" knows only that it stayed red, and "Replay-style instruments are a distinct kind…" knows only that this red is the kind that could mean a loss. Both are cheaper to trust; neither can tell a human that breakeven was ~50% and the data said 28%.

**Where it fails, stated so it can be judged.** A builder that cannot make a spec pass has every incentive to call the red a refutation. The structure limits that (it must cite the bar and the value, both of which the spec itself encodes) but cannot prevent it; a human reading five of these will know quickly whether the channel is honest, and that is the assumption beneath.

**Cost.** A report-file convention, a postflight parser, and one new non-reserved section heading that the content guard must allow and the gate must ignore.

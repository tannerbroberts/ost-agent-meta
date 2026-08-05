---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  A test whose bold pre-commitment lead-in is wrapped across a line break
  classifies identically to the same text unwrapped — for `bound`, `instruction`
  and `prose` alike — and the only tests counted `absent` are those with no
  pre-commitment paragraph at all.
instrument: npx vitest run test/ost/threshold-lead-in-wrap.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Not whether anyone wants the count, but whether the count means what it says.

**The assumption under test.** That `debt`'s four-way classification of a pre-commitment paragraph reads the threshold rather than its formatting. The parent solution's own body records that it does not, twice, both times by accident and both times in a live vault:

- Pass 6 (2026-07-25): a `tetrix-ost` node whose lead-in read `**Pre-commit before looking, and this is a bar rather than an instruction to set one:**` broken over two lines counted `absent`; rewritten onto one line, with no word of the threshold changed, the same node counted `bound`.
- Pass 7 (2026-07-26): a node carrying a minimum sample, a numeric bar and an explicit revert condition — `**Pre-committed threshold: 20 arrivals … at all.**`, bold spanning two lines — counted `absent`. Same rewrite, same move to `bound`.

The extractor's lead-in pattern requires the bold `**…pre-commit…**` marker to sit at the start of the paragraph, and a hard-wrapped bold span does not.

**Why this is the test and not the one already attached.** The existing sibling, "Do named unfixed thresholds actually get fixed", asks whether naming an unfixed threshold causes anyone to fix it — a longitudinal question about people, and untouched by this. This one asks whether the naming is correct in the first place. A feature that reports a number can be read either way, and only one of those two questions has an exit code.

**What is red today, and why that is the strongest kind of red.** The command names behaviour that does not exist: a classifier insensitive to where prose formatting put a line break. It is not red because a file is missing — the parent solution shipped as v0.10.0 and the classifier is live — but because the shipped classifier gives two different answers for one threshold. A spec asserting wrapped and unwrapped forms classify identically fails against today's extractor, by observation rather than by prediction.

**What a green result does NOT settle.** It settles that the count is no longer a formatting artefact. It says nothing about whether the count is *acted on* — that is the sibling test — and nothing about whether the four-way split is the right taxonomy. It also cannot recover the historical numbers: every `absent` count this feature has ever published remains a floor rather than a measurement, including the 12 recorded in this vault, and a human deciding what those 12 were should not read a green here as re-counting them.

**Why the sequencing caution in the parent body does not block this.** Pass 6 flagged rather than fixed the defect, on the argument that changing the extractor changes a published number and the right order is to decide what the number means first. That argument is about *shipping the fix*; it is not an argument against having a command that says whether the fix is in. Writing the spec makes the defect falsifiable and leaves the decision exactly where pass 6 left it.

**Lane: compute-only.** Two committed markdown fixtures and one classifier call; no person is the measurement.

⚠️ Unvalidated. Proposed by an unattended pass from its parent's own recorded observations. Nothing here was run.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/threshold-lead-in-wrap.test.ts` — No test files found, exiting with code 1

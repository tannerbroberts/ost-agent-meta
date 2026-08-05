---
type: Solution
status: unvalidated
source: 'agent-ideation:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Do named unfixed thresholds actually get fixed]]
[[A wrapped pre-commitment lead-in is read, so the absent count stops being a formatting artefact]]

**The idea.** `ost-agent debt` (and `status`) name every assumption test whose
pre-commitment reads as an instruction rather than a commitment — no number, no
bound, opening on *Fix…* / *Decide…* / *Choose…* — and total them. Report only.
Nothing is blocked, nothing is refused, nothing is rewritten.

**Approach.** The extractor already returns the paragraph. This adds one shallow
classification on top of it, in the same spirit as the rest of the coverage feature:
it never asks whether the threshold is *good*, only whether it is a threshold.

**How it differs from its siblings.** [[Refuse to record a result against a threshold that was never fixed]]
enforces; [[Make the threshold a field the node carries, not a sentence in its prose]]
restructures. This one only looks. It is deliberately the weakest of the three, and
it is proposed first for that reason: the parent opportunity's own caveat is that a
mechanical rule here will be wrong at the edges, and a report that is wrong is a
nuisance while a refusal that is wrong is a wall.

**Size:** an afternoon. One function, two counters, two lines of output — the same
shape as the v0.9.0 increment that produced the finding.

**Trade-off.** A report nobody reads changes nothing, and this tree already has one
unrun assumption test about exactly that failure mode
([[Does the side-by-side change what a reviewer does about a threshold]]). Building
two reports before learning whether the first one is read would be a pattern worth
naming out loud.

**Cheapest disconfirmer.** [[Do named unfixed thresholds actually get fixed]] — name
them once, wait, and count how many are still unfixed.

⚠️ Unvalidated. Proposed by an agent from a mechanical census of its own two vaults.

## Shipped as v0.10.0, and this vault never recorded it — 2026-07-25 (pass 6)

**Hygiene note first, because it is the more useful finding.** The last standing
briefing argued *against* building this next, and the release notes for v0.10.0 show
it was built anyway — on `main` as `019780f`, five commits before this pass started.
Nothing in this vault records that. The tree carried a briefing recommending against
a thing that had already shipped, for a full cycle. **The mapping step is not
automatic**, and a pass that ships without mapping leaves the tree describing a
product that no longer exists. Filed here rather than as a new node because it is one
occurrence; a second would make it a pattern worth its own opportunity.

**What v0.10.0 actually does.** `ost-agent debt` classifies every assumption test's
pre-commitment paragraph into four kinds that sum to the total — `bound` (a number,
or a comparison in words), `instruction` (opens on a deferring verb with no bar in
it), `prose` (neither, and often a perfectly good falsifiable bar), `absent` (no
paragraph at all) — and `ost-agent status` reports the count in one line. Report only:
nothing is blocked, refused, or rewritten, on the argument that a wrong report is a
nuisance while a wrong refusal is a wall. A bar beats an imperative opening, so
*"Decide the bar; last time 5 of 20 booked"* reads as `bound`.

**It has now been run against both live vaults twice, and it changed a decision.**
This pass's tetrix census — 29 tests, 7 bound, 4 prose, 18 instruction, 0 absent —
is what the sibling briefing's §4 rests on, and it is why the agent writing new
assumption tests over there was made to write real bars. That is this feature paying
for itself in the only currency that counts: a different action taken.

**A defect found by using it, this pass.** The extractor's lead-in pattern requires
the bold `**…pre-commit…**` marker to sit at the start of the paragraph; a
pre-commitment whose bold lead-in is **wrapped across a line break** by prose
formatting is classified `absent` rather than read. Observed live: a node written in
`tetrix-ost` this pass with the lead-in *"**Pre-commit before looking, and this is a
bar rather than an instruction to set one:**"* broken over two lines counted as
`absent` until it was rewritten onto one line, at which point the same threshold
counted as `bound`. Consequence: **the `absent` count is an over-count of a
formatting accident**, and in the vault where 12 tests currently read `absent` some
unknown share of them may carry real thresholds nobody can see. This is the third
line-wrapping defect this loop has found (two dangling wiki-links, now one threshold),
which makes hard-wrapped prose a recurring source of silent misreads rather than a
typo. Flagged, not fixed — changing the extractor changes a published number.

## Issues
- 2026-07-26 **Second confirmed sighting of the line-wrap misread, this time reproduced
live and by accident** (autonomous loop, pass 7). Pass 6 recorded that the extractor
classifies a bold pre-commitment lead-in as `absent` when prose formatting has wrapped it
across a line break. This pass wrote a new assumption test in the tetrix vault whose
pre-commitment reads `**Pre-committed threshold: 20 arrivals … at all.**` with the bold
spanning two lines — a test carrying a minimum sample, a numeric bar and an explicit
revert condition — and `debt` called it `absent`. Rewriting it as `**Pre-committed
threshold.** 20 arrivals …`, with the lead-in on one line and not one word of the
threshold changed, moved it to bound. **The consequence for every number this feature has
ever published: the `absent` count is a floor, not a measurement.** In the tetrix vault
that count is currently 0 and in this vault it is 12, and an unknown share of those 12 may
carry real thresholds that nobody can see. Flagged rather than fixed, for the reason pass 6
gave and which still holds: changing the extractor changes a published number, and the
right sequence is to decide what the number means before improving how it is counted.

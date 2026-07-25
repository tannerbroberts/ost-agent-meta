# External review — five-dimension audit of this vault (2026-07-24)

Five independent reviewer passes (opportunity layer, solution layer, assumption-test
layer, evidence base, strategic utility) run by Claude Code at the operator's request.
Rung honesty: this is **model assertion** — an AI critique, not external customer
evidence. Its value is diagnostic, not evidentiary.

Scores: opportunities 6/10 · solutions 6.5/10 · assumption tests 7/10 ·
evidence base 3/10 · strategic utility 5/10 · overall ~5.5/10.

## Headline finding

The tree names seven of its own pathologies as content and operationally exhibits
all seven: (1) provenance gap — 23 artifacts feed 149 nodes, 65% founder-authored,
35% agent-authored, 0% external; (2) nothing kills a candidate — 0 archived/killed
statuses, 0 nodes carry kill criteria including the kill-criteria node itself;
(3) candidates all look alike — uniform 3-per-opportunity batches from one ideator
in one template (`minSolutionsPerOpportunity: 3` configures sprawl in);
(4) building crowds out evidence search — builder shipped code while zero external
probes ran; (5) unvalidated pileup — 148/149 unvalidated, 60 tests defined, 0 run;
(6) pass never done — mapped-ledger dead-end confirmed in two vaults;
(7) can't tell human from agent edits — 72/72 commits under the founder's identity,
zero distinguishable review activity.

## Layer findings (condensed)

- **Outcome (pre-retune):** four fused goals phrased as team activity; no customer
  behavior, no metric. Retuned 2026-07-24 (prior mandate in root History).
- **Opportunities:** top level 13-wide, organized by inbox chronology not customer
  journey; near-synonym siblings (walk-away trust vs unattended-worry); persona
  oscillates founder-operator ↔ hypothetical npm operator with nothing marking which;
  2 genuinely observed opportunities are the layer's best (Obsidian corruption,
  never-done). Solutions-in-disguise: hijackable-capability (self-flagged), raw-usage
  summaries, never-done (bundles two defects + an economics need).
- **Solutions:** per-node craft excellent (contrast sections, trade-offs, tagged
  riskiest assumptions). Set-level: siblings frequently complementary layers of one
  architecture, not competing bets (append-only/git/no-push trio; allowlist/manifest/
  red-team trio); judge/critic bet appears under 3 opportunities; digest bet under 2;
  ~55/66 are build-a-feature — no buy/adopt lane, no do-nothing lane; newest cohort
  drifts into design-doc spec-creep; 6 solutions shipped with no assumption test.
- **Assumption tests:** 60/60 pre-committed thresholds (~5 soft); category skew
  feasibility 28 / desirability 20 / usability 6 / viability 6; exactly one money
  test; formulaic 1-test-per-solution (none has two — riskiest asserted, not
  selected); ~10 tests are secretly multi-week projects; ~10 presuppose an operator
  population that doesn't exist; 4 near-identical trust-delta interview studies
  could be one protocol.
- **Evidence base:** citations verify (no fabrication); ladder defined as product
  idea, used once in practice (root only) pre-fix; History on 1/149 nodes; staleness
  purely aspirational; 7 inbox items consumed but uncited (evidence swallowed);
  5 nodes' source frontmatter destroyed (YAML `>-` bug) by merge 57c3745 — the one
  material append-only violation; repaired 2026-07-24 under distinct author.
- **Strategy:** effort inverted — 41 nodes (~28%) harden trust for operators who
  don't exist while the demand branch gets 27; the correct first target was known
  but encoded only in a prose Issues note; no sizing anywhere; 13-front sprawl vs
  Torres one-target-go-deep. Run-first consensus: **Cold-offer test** (zero build,
  pre-committed kill threshold, every reply is the vault's first external evidence),
  then two-week recruiting test; pre-order probe gated until a traffic source exists.

## Missing strategic branches (added 2026-07-24, evidence-debt-gated)

Buyer/ICP · alternatives/status-quo ("why not Claude + Obsidian by hand?") ·
pricing/unit-of-value · distribution · the existential paradox (does automating
tree maintenance destroy the value practitioners get from maintaining one?).

## Product bugs surfaced by this review (for ~/dev/OST-Agent)

- `ost_set_evidence` exists in src/security/tools.ts but is absent from the CLI
  `tool` allowlist — the ladder cannot be practiced through the shipped surface.
- Merge/port path serializes multiline `source:` to literal `'>-'` (5 nodes hit).
- Nothing surfaces the target opportunity: `ost_next_work` treats 13 rows as peers.
- `minSolutionsPerOpportunity` acts as a quota generator; no distinctness pressure,
  no buy/adopt/do-nothing lanes in P3 prompts; P4 emits exactly 1 test/solution.
- No staleness mechanism, no kill-criteria affordance, no human/agent git identity
  separation (agent commits as the founder).

## Addendum — bugs observed live during the 2026-07-24 hard-fix pass itself

- The 0.1.3 serializer DROPS the `evidence:` frontmatter field whenever any tool
  rewrites a node (annotate/status/append/link); the `#evidence/<rung>` tag survives
  only because unknown tags are passed through. Until the vault runs a build where
  node.ts knows the field, every agent pass will silently strip rung frontmatter.
- `ost_create_node`@0.1.3 accepted and silently discarded the `evidence` input
  (11 nodes created without the rung they were given) — schema drift between the
  published CLI and src/security/tools.ts, and no input validation error either way.

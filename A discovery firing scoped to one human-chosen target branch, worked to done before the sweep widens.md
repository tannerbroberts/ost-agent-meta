---
type: Solution
status: shipped
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Mechanism:** a human-set target (a `target:` field in `ost.config.yaml`, or `ost-agent target <opportunity title>` on the CLI — human-set to honor the MUST NOT at `ruleset.ts:142` against auto-selecting a target opportunity). `ost_next_work` gains a `scope` parameter that filters every bucket to the target opportunity's subtree, plus the evidence records whose best-match candidate lands there; `/ost-pass` reads the target and works that branch until its buckets are empty before touching anything else. When no target is set, today's whole-tree sweep is the unchanged fallback. Render the ruleset's `cadence` block (which already prescribes "select a single target opportunity at a time") into SKILL.md so the running agent finally sees it.

**Why this shape:** it matches Torres's prioritize-then-ignore-other-branches procedure exactly, gives the operator the one-branch mental model they asked for, and keeps target selection a human act — the agent's added power is only the discipline to stay inside the choice.

**Precedent in-repo:** the build loop already has per-item focus (`src/loop/claim.ts` — a pass claims the one briefing item it is building). This is the discovery-side equivalent, one level up.

## Shipped

Built and merged to main as PR #100 (commit 666f383, 2026-08-11), on the operator's direct mandate ("we actually need to work those opportunities"). What shipped, against the mechanism sketch above: `discovery.target` in `ost.config.yaml` (human-set; no tool can write it and `ost_next_work` deliberately grew NO input parameter for it, honoring the auto-select MUST NOT structurally); a scoped sweep in `computeNextWork` where every done-blocking bucket and `done` itself cover the target opportunity's subtree; per-list exclusion accounting in `scope.excluded` so scoping is never silent; a mistyped target runs UNSCOPED with `resolved: false` and a summary warning rather than narrowing to nothing; the ruleset's cadence block ("select a single target opportunity at a time") now renders into SKILL.md for the first time; /ost-pass instructs a scoped firing to work the branch alone. Pinned by 9 tests in `test/mcp/scoped-next-work.test.ts`. Setting the first target remains the operator's move — one line in the meta vault's `ost.config.yaml`.

## History
- 2026-08-11 status: (none) → shipped — PR #100 merged to main 2026-08-11 (commit 666f383); behavior pinned by test/mcp/scoped-next-work.test.ts (9 tests). Shipped-not-validated: no operator has yet run a targeted pass.
